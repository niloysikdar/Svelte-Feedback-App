<script>
    import { FeedbackStore } from "../stores";
    export let data = {};

    const handleDelete = (id) => {
        FeedbackStore.update((currentData) => {
            return currentData.filter((item) => item.id !== id);
        });
    };
</script>

<style>
    .card {
        background-color: #fff;
        color: #333;
        border-radius: 10px;
        padding: 40px 50px;
        margin: 20px 0;
        position: relative;
    }
    .num-display {
        position: absolute;
        top: -10px;
        left: -10px;
        width: 50px;
        height: 50px;
        background: #ff6a95;
        color: #fff;
        border: 1px #eee solid;
        border-radius: 50%;
        padding: 10px;
        text-align: center;
        font-size: 19px;
    }
    .close {
        position: absolute;
        top: 5px;
        right: 10px;
        font-size: 20px;
        padding: 7px;
        cursor: pointer;
        background: none;
        border: none;
    }

    @media (max-width: 700px) {
        .card {
            padding: 35px 30px;
        }
    }
</style>

<div class="card">
    <div class="num-display">{data.rating}</div>
    <button class="close" on:click={() => handleDelete(data.id)}>X</button>
    <p class="text-display">{data.text}</p>
</div>
