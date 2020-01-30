<script>
	import FlashCard from './FlashCard.svelte';
	import Stave from './Stave.svelte';
	import { slide } from 'svelte/transition';

	export let num_problems = 100;

    var random_notes = [];
    for (var i=0; i<13; i++) {
        random_notes.push([Math.random(), i, 'stave', 'keys']);
        // random_notes.push([Math.random(), i, 'stave', 'letter']);
        // random_notes.push([Math.random(), i, 'keys', 'letter']);
        // random_notes.push([Math.random(), i, 'keys', 'stave']);
        // random_notes.push([Math.random(), i, 'letter', 'stave']);
        // random_notes.push([Math.random(), i, 'letter', 'keys']);
    }
    random_notes.sort();
    let notes = random_notes.splice(0, num_problems).map(function(f) {
	  f.splice(0, 1);
	  return f;
    });

    const treble_notes = [
        "B",
        "A",
        "G",
        "F",
        "E",
        "D",
        "C",
        "B",
        "A",
        "G",
        "F",
        "E",
        "D",
        "C",
        "B",
    ];

    let prompt_index = 0;
    let answer_index = -1;

	function show_next() {
        answer_index += 1;
        prompt_index += 1;
	}
</script>

<style>
	p {
		font-size: 30pt;
	}
	button {
		width: 200px;
	}
</style>

<p>
    <Stave>
        </Stave>
    {#if answer_index == -1}
      <div
        transition:slide="{{ delay: 500, duration: 500 }}"
        style="padding: 10px;"
        >&nbsp;</div>
    {/if}
	{#each notes as note, i}
	  {#if i === prompt_index || i === answer_index}
        <div
            transition:slide="{{ delay: 500, duration: 500 }}"
            style="padding: 10px;"
            >
        <FlashCard
             {i}
             note={note[1]}
             show_answer={i === answer_index}
             />
        </div>
	  {/if}
	{/each}
</p>
