<script>
    import {FeedbackStore} from "../stores";

    $: count = $FeedbackStore.length;
    $: average = ($FeedbackStore.reduce((a, {rating}) => a + rating, 0) / count).toFixed(2);

</script>

<div class="feedback-stats">
    <h4>{count} reviews</h4>
    <h4>Ratings average: {average}</h4>
</div>

<style>
    .feedback-stats {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>