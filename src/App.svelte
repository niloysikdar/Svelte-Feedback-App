<script>
	import FeedbackList from "./components/FeedbackList.svelte";
	import { FeedbackData } from "./FeedbackData";
	let feedbackData = FeedbackData;

	$: feedbacklistLength = feedbackData.length;
	$: averageRating =
		feedbackData.reduce((a, { rating }) => a + rating, 0) /
			feedbacklistLength || 0;

	const handleDelete = (e) => {
		const itemId = e.detail;
		feedbackData = feedbackData.filter((item) => item.id !== itemId);
		console.log(e.detail);
	};
</script>

<main class="container">
	<h2>{feedbacklistLength}</h2>
	<h2>{averageRating}</h2>
	<FeedbackList {feedbackData} on:delete-feedback={handleDelete} />
</main>
