<script>
	import FeedbackList from "./components/FeedbackList.svelte";
	import FeedbackStats from "./components/FeedbackStats.svelte";
	import FeedbackForm from "./components/FeedbackForm.svelte";

	import { FeedbackData } from "./FeedbackData";
	let feedbackData = FeedbackData;

	const addNewFeedback = (e) => {
		feedbackData = [e.detail, ...feedbackData];
	};
</script>

<main class="container">
	<FeedbackForm on:new-feedback={addNewFeedback} />
	<FeedbackStats />
	<FeedbackList />
</main>
