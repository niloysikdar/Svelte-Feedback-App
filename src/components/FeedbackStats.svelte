<script>
    export let count;
    export let average;
</script>

<style>
    .feedback-stats {
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: wrap;
        padding: 10px 20px;
    }

    .feedback-stats h4 {
        font-size: 20px;
        font-weight: 500;
    }
</style>

<div class="feedback-stats">
    <h4>Feedback Count: {count}</h4>
    <h4>Average Rating: {average}</h4>
</div>
