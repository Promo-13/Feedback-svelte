<script>
  import FeedbackForm from "./components/FeedbackForm.svelte";
  import FeedbackList from "./components/FeedbackList.svelte";
  import FeedbackStats from "./components/FeedbackStats.svelte";

  let feedback = [
    {
      id: 1,
      rating: 10,
      text: "lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
    },
    {
      id: 2,
      rating: 8,
      text: "cat ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
    },
    {
      id: 3,
      rating: 6,
      text: "dog ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
    },
    {
      id: 4,
      rating: 4,
      text: "lion ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
    },
    {
      id: 5,
      rating: 2,
      text: "tiger ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
    },
  ];

  $: count = feedback.length;
  $: average = feedback.reduce((a, {rating}) => a + rating, 0) / feedback.length;

  const addFeedback = (e) => {
	const newFeedback = e.detail;
	feedback = [newFeedback, ...feedback];
  };

  const deleteFeedback = (e) => {
    const itemId = e.detail;
    feedback = feedback.filter((fb) => fb.id !== itemId);
  };
</script>

<main class="container">
  <FeedbackForm on:add-feedback={addFeedback}/>
  <FeedbackStats {count} {average} />
  <FeedbackList {feedback} on:delete-feedback={deleteFeedback} />
</main>
