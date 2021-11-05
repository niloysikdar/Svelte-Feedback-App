<script>
    import { v4 as uuidv4 } from "uuid";
    import { FeedbackStore } from "../stores";
    import RatingSelect from "./RatingSelect.svelte";
    import SubmitButton from "./SubmitButton.svelte";

    let text = "";
    let isDisabled = true;
    let rating = 10;
    const minLen = 10;
    let message;

    const handleInputChange = () => {
        if (text.trim().length < minLen) {
            const remaining = minLen - text.trim().length;
            message = `Text must be at least ${minLen} characters long, ${remaining} remaining`;
            isDisabled = true;
        } else {
            message = "";
            isDisabled = false;
        }
    };

    const handleRatingSelect = (e) => (rating = e.detail);

    const handleSubmit = () => {
        if (text.trim().length >= minLen) {
            const newData = {
                id: uuidv4(),
                rating: +rating,
                text,
            };
            FeedbackStore.update((currentData) => {
                return [newData, ...currentData];
            });
            text = "";
            isDisabled = true;
        }
    };
</script>

<style>
    .card {
        background-color: #fff;
        color: #333;
        border-radius: 10px;
        padding: 30px 50px;
        margin: 20px 0;
        position: relative;
    }
    header {
        margin: auto;
    }
    header h2 {
        font-size: 22px;
        font-weight: 600;
        text-align: center;
    }
    .input-group {
        display: flex;
        border: 1px solid #ccc;
        padding: 8px 10px;
        border-radius: 8px;
        margin-top: 15px;
    }
    input {
        flex-grow: 2;
        border: none;
        font-size: 16px;
    }
    input:focus {
        outline: none;
    }
    .message {
        padding-top: 10px;
        text-align: start;
        color: rebeccapurple;
    }

    @media (max-width: 700px) {
        .card {
            padding: 15px;
        }
    }
</style>

<div class="card">
    <header>
        <h2>Please provide your feedback about our service</h2>
    </header>
    <form on:submit|preventDefault={handleSubmit}>
        <RatingSelect on:rating-select={handleRatingSelect} />
        <div class="input-group">
            <input
                type="text"
                bind:value={text}
                on:input={handleInputChange}
                placeholder="Something about your experience and feedback" />
            <SubmitButton disabled={isDisabled} type="submit" />
        </div>
        {#if message}
            <div class="message">{message}</div>
        {/if}
    </form>
</div>
