<script>
export let title;

	let numbers = [];
	let number = '';

	function addNumber() {
        numbers = [...numbers, parseInt(number)];
        number = '';
	}

    $: sum = numbers.reduce((t, n) => t + n, 0);
    
    	let user = { loggedIn: false };

	function toggle() {
		user.loggedIn = !user.loggedIn;
    }
    
    let cats = [
		{ id: 'J---aiyznGQ', name: 'Keyboard Cat' },
		{ id: 'z_AbfPXTKms', name: 'Maru' },
		{ id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat' }
	];
</script>
<h3>
{ title }
</h3>
<p>{numbers.join(' + ')} = {sum}</p>
<p>
	<input type="text" placeholder="Enter Number" bind:value="{number}">
</p>
<button on:click={addNumber}>
	Add a number
</button>

{#if user.loggedIn}
	<button on:click={toggle}>
		Log out
	</button>
{:else}
	<button on:click={toggle}>
		Log in
	</button>
{/if}

<ul>
	{#each cats as cat}
		<li><a target="_blank" href="https://www.youtube.com/watch?v={cat.id}">
			{cat.name}
		</a></li>
	{/each}
</ul>