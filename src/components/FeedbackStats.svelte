<script>
    import { FeedbackStore } from "../stores";

    $: feedbacklistLength = $FeedbackStore.length;
    $: averageRating = (
        $FeedbackStore.reduce((a, { rating }) => a + rating, 0) /
            feedbacklistLength || 0
    ).toFixed(2);
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
    <h4>Feedback Count: {feedbacklistLength}</h4>
    <h4>Average Rating: {averageRating}</h4>
</div>
