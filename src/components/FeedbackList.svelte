<script>
    import { scale, fade } from 'svelte/transition';
    import FeedbackItem from './FeedbackItem.svelte'
    export let feedback = [];
</script>

{#each feedback as fb (fb.id)}
    <div in:scale out:fade="{{ duration: 200 }}">
        <FeedbackItem item={fb} on:delete-feedback />
    </div>
{/each}
