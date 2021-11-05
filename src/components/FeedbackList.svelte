<script>
    import { scale, fade } from "svelte/transition";
    import FeedbackItem from "./FeedbackItem.svelte";

    export let feedbackData = [];
</script>

{#each feedbackData as data (data.id)}
    <div in:scale={{ duration: 500 }} out:fade={{ duration: 500 }}>
        <FeedbackItem {data} on:delete-feedback />
    </div>
{/each}
