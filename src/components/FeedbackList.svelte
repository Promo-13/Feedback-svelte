<script>
    import {onMount, onDestroy} from 'svelte';
    import {FeedbackStore} from '../stores';
    import {fade, scale} from "svelte/transition";
    import FeedbackItem from "./FeedbackItem.svelte";
    let feedback = [];
    
    const unsubscribe = FeedbackStore.subscribe((value) => {
        feedback = value;
    });

    onMount(() => {
        console.log('FeedbackList mounted');
    });

    onDestroy(() => {
        unsubscribe();
    });


</script>

{#each feedback as fb (fb.id)}
    <div in:scale out:fade={{duration: 500}}>
        <FeedbackItem item={fb} />
    </div>
{/each}