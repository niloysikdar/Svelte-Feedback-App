<script>
    import SubmitButton from "./SubmitButton.svelte";

    let text = "";
    let isDisabled = true;
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
        flex-direction: row;
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
</style>

<div class="card">
    <header>
        <h2>Please provide your feedback about our service</h2>
    </header>
    <form>
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
