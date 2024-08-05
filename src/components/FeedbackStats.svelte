<script>
    export let count;
    export let average;
</script>

<div class="feedback-stats">
    <h4>Count: {count}</h4>
    <h4>Average: {average}</h4>
</div>

<style>
    .feedback-stats {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>
