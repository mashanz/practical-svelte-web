<script>
	const layers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

	let y = 0;
</script>

<svelte:window bind:scrollY={y} />

<header>
	<h1>PRACTICAL SVELTE</h1>
</header>

<div class="parallax-container">
	{#each layers as layer}
		<img
			style="transform: translate(0,{(-y * layer) / (layers.length - 1)}px)"
			src="/layer/{layer}.png"
			alt="parallax layer {layer}"
		/>
	{/each}
</div>

<div class="text">
	<div class="foreground">
		<!-- You have scrolled {y} pixels -->
	</div>
</div>

<style>
	header {
		position: absolute;
		top: 0;
		left: 0;
		z-index: 100;
		width: 100%;
		height: 50px;
		background-color: rgb(10, 10, 10);
		color: white;
		padding: 0 0 0 0.5em;
		box-sizing: border-box;
	}
	h1 {
		font-family: monospace;
		margin: 0;
		padding: 0;
		line-height: 50px;
	}
	.parallax-container {
		position: fixed;
		width: 2500px;
		height: 100%;
		left: 50%;
		transform: translate(-50%, 0);
	}

	.parallax-container img {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		will-change: transform;
	}

	.parallax-container img:last-child::after {
		content: '';
		position: absolute;
		width: 100%;
		height: 100%;
		background: rgb(45, 10, 13);
	}

	.text {
		position: relative;
		width: 100%;
		height: 250vh;
		color: rgb(10, 10, 10);
		text-align: center;
		padding: 4em 0.5em 0.5em 0.5em;
		box-sizing: border-box;
		pointer-events: none;
	}

	.foreground {
		position: absolute;
		top: 850px;
		left: 0;
		width: 100%;
		height: calc(100% - 712px);
		background-color: rgb(10, 10, 10);
		color: white;
		padding: 50vh 0 0 0;
	}

	:global(body) {
		margin: 0;
		padding: 0;
		background-color: rgb(10, 10, 10);
	}
</style>
