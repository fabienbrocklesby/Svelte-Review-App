<script>
	import FeedbackForm from './components/FeedbackForm.svelte';
	import FeedbackList from './components/FeedbackList.svelte';
	import FeedbackStats from './components/FeedbackStats.svelte';

	let feedback = [
		{
			id: 1,
			rating: 10,
			text: 'Occaecat laboris minim consectetur aliquip adipisicing occaecat sit magna. Eiusmod consectetur Lorem aliquip cillum sint enim dolor amet eiusmod consectetur ullamco.',
		},
		{
			id: 2,
			rating: 9,
			text: 'Mollit consectetur excepteur sit minim est reprehenderit proident eiusmod ullamco mollit consequat sunt ea eu. Eiusmod consectetur Lorem aliquip cillum sint enim dolor amet eiusmod consectetur ullamco.',
		},
		{
			id: 3,
			rating: 8,
			text: 'Eiusmod ipsum consequat tempor Lorem officia nostrud irure adipisicing consequat ad commodo. Duis amet voluptate labore sint. Eiusmod consectetur Lorem aliquip cillum sint enim dolor amet eiusmod consectetur ullamco.',
		},
	]

	$: count = feedback.length;
	$: average = feedback.reduce((a, {rating}) => a + rating, 0) / feedback.length;

	const addFeedback = (e) => {
		const newFeedback = e.detail;
		feedback = [newFeedback, ...feedback];
	}

	const deleteFeedback = (e) => {
		const itemId = e.detail;

		feedback = feedback.filter((item) => item.id !=itemId);
	}
</script>

<main class="container">
	<FeedbackForm on:add-feedback={ addFeedback } />
	<FeedbackStats {count} {average} />
	<FeedbackList {feedback} on:delete-feedback={deleteFeedback} />
</main>
