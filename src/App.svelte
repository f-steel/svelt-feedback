<script>
	import FeedbackList from "./components/feedbackList.svelte";
	import FeedbackStats from "./components/FeedbackStats.svelte";
	import Feedbackform from "./components/Feedbackform.svelte";
	let feedback = [
		{
			id: 1,
			rating: "10",
			text: "Great job! Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed euismod, nisl ac tincidunt consequat, mauris justo efficitur nunc, id ultrices nunc nunc nec nunc. Nulla facilisi. Sed auctor, nunc in efficitur tincidunt, nisl nunc tincidunt nunc, nec tincidunt nunc nunc nec nunc.",
		},
		{
			id: 2,
			rating: "9",
			text: "Good job! Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed euismod, nisl ac tincidunt consequat, mauris justo efficitur nunc, id ultrices nunc nunc nec nunc. Nulla facilisi. Sed auctor, nunc in efficitur tincidunt, nisl nunc tincidunt nunc, nec tincidunt nunc nunc nec nunc.",
		},
		{
			id: 3,
			rating: "8",
			text: "This is a really good piece of work! Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed euismod, nisl ac tincidunt consequat, mauris justo efficitur nunc, id ultrices nunc nunc nec nunc. Nulla facilisi. Sed auctor, nunc in efficitur tincidunt, nisl nunc tincidunt nunc, nec tincidunt nunc nunc nec nunc.",
		},
		{
			id: 4,
			rating: "7",
			text: "This has changed my life, amazing! Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed euismod, nisl ac tincidunt consequat, mauris justo efficitur nunc, id ultrices nunc nunc nec nunc. Nulla facilisi. Sed auctor, nunc in efficitur tincidunt, nisl nunc tincidunt nunc, nec tincidunt nunc nunc nec nunc.",
		},
	];

	$: count = feedback.length;
	$: average =
		feedback.reduce((acc, curr) => acc + parseInt(curr.rating), 0) /
		feedback.length;

	const deleteFeedback = (e) => {
		const itemId = e.detail;
		feedback = feedback.filter((fb) => fb.id !== itemId);
	};
</script>

<main class="container">
	<Feedbackform />
	<h1>Feedback</h1>
	<FeedbackStats {count} {average} />
	<FeedbackList {feedback} on:delete-feedback={deleteFeedback} />
</main>

<style>
</style>
