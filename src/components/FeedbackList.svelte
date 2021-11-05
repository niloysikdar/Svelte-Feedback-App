<script>
    import FeedbackItem from "./FeedbackItem.svelte";

    export let feedbackData = [];
</script>

<h2>Feedback List</h2>
{#each feedbackData as data (data.id)}
    <FeedbackItem {data} on:delete-feedback />
{/each}
