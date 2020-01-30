<script>
    import FlashForward from './FlashForward.svelte';
    import Launch from './Launch.svelte';

	let name = 'music maker';

    let launched = true; // false;

    let num_problems = 100;
    let op_mult = true;
    let op_div = false;

    function handle_launch(e)
    {
        launch = false;
    }
</script>

<h1>Hi {name}!</h1>

{#if launched}
<FlashForward
    {num_problems}
    />
{:else}
<Launch
    bind:launched={launched}
    bind:num_problems={num_problems}
    bind:op_mult={op_mult}
    bind:op_div={op_div}
    />
{/if}
