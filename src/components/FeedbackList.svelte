<script>
    import FeedbackItem from "./FeedbackItem.svelte";

    export let feedbackData = [];
</script>

{#each feedbackData as data (data.id)}
    <FeedbackItem {data} on:delete-feedback />
{/each}
