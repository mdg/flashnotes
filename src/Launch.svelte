<script>
    export let launched = false;
    // export let op_add = false;
    // export let op_sub = false;
    export let op_mult = true;
    export let op_div = false;
    export let num_problems = 100;

    function toggle_op_add()
    {
        op_add = !op_add;
    }

    function toggle_op_mult()
    {
        op_mult = !op_mult;
        if (!op_mult) {
            op_div = true;
        }
    }

    function toggle_op_div()
    {
        op_div = !op_div;
        if (!op_div) {
            op_mult = true;
        }
    }

    function op_state_class(op_state)
    {
        return op_state ? "op_selected" : "op_unselected";
    }

    function handle_launch(e)
    {
        launched = true;
    }
</script>

<style>
	p {
		font-size: 24pt;
	}

    button.operation {
        width: 110px;
        font-weight: bold;
    }

    button.op_selected {
        color: #ffffff;
        background-color: #119911;
    }

    button.op_unselected {
        color: #222222;
        background-color: #b0b0b0;
    }

    input {
        width: 100px;
    }
</style>

<p>
    Which operations?
</p>
<p>
    <!--
    <button class="operation" on:click={toggle_op_add}>+</button>
    &nbsp;
    <button class="operation" on:click={toggle_op_sub}>-</button>
    &nbsp;
    -->
    <button class="operation {op_state_class(op_mult)}" on:click={toggle_op_mult}>x</button>
    &nbsp;
    <button class="operation {op_state_class(op_div)}" on:click={toggle_op_div}>÷</button>
</p>

<p>
    # of Problems? <input bind:value={num_problems} />
</p>

<p>
	<button id=go_button on:click={handle_launch}>
		&nbsp;
		go!
		&nbsp;
	</button>
</p>
