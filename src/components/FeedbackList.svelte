<script>
    import { FeedbackStore } from "../stores";
    import { scale, fade } from "svelte/transition";
    import FeedbackItem from "./FeedbackItem.svelte";
</script>

{#each $FeedbackStore as data (data.id)}
    <div in:scale={{ duration: 500 }} out:fade={{ duration: 500 }}>
        <FeedbackItem {data} />
    </div>
{/each}
