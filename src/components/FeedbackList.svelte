<script>
    export let feedbackData = [];
</script>

<h2>Feedback List</h2>
{#each feedbackData as data (data.id)}
    <p>{data.id}: {data.text}</p>
{/each}
