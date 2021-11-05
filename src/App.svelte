<script>
	import FeedbackList from "./components/FeedbackList.svelte";
	import FeedbackStats from "./components/FeedbackStats.svelte";
	import FeedbackForm from "./components/FeedbackForm.svelte";

	import { FeedbackData } from "./FeedbackData";
	let feedbackData = FeedbackData;

	$: feedbacklistLength = feedbackData.length;
	$: averageRating = (
		feedbackData.reduce((a, { rating }) => a + rating, 0) /
			feedbacklistLength || 0
	).toFixed(2);

	const handleDelete = (e) => {
		const itemId = e.detail;
		feedbackData = feedbackData.filter((item) => item.id !== itemId);
	};

	const addNewFeedback = (e) => {
		feedbackData = [e.detail, ...feedbackData];
	};
</script>

<main class="container">
	<FeedbackForm on:new-feedback={addNewFeedback} />
	<FeedbackStats count={feedbacklistLength} average={averageRating} />
	<FeedbackList {feedbackData} on:delete-feedback={handleDelete} />
</main>
