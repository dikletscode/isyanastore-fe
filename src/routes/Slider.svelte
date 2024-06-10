<script>
	import { spring } from 'svelte/motion';
	import logo from '$lib/images/ISYANA-SARASVATI-Isyana-Photo-2.jpg';

	let count = 0;

	const displayed_count = spring();
	$: displayed_count.set(count);
	$: offset = modulo($displayed_count, 1);

	/**
	 * @param {number} n
	 * @param {number} m
	 */
	function modulo(n, m) {
		// handle negative numbers
		return ((n % m) + m) % m;
	}
</script>

<section class="slider-wrap">
	<div class="slider">
		<div>
			<h3>Listen now! (Link to streaming platforms)</h3>
			<h2>Isyana Sarasvati's Debut Album <span class="higlight">"ISYANA"</span> is HERE!</h2>
			<h4>UP to 80% OFF</h4>
			<div class="control">
				<div class="dot active" />
				<div class="dot" />
				<div class="dot" />
			</div>
		</div>
		<img src={logo} alt="SvelteKit" height="300" width="300" />
	</div>

	<!-- <button on:click={() => (count -= 1)} aria-label="Decrease the counter by one">
		<svg aria-hidden="true" viewBox="0 0 1 1">
			<path d="M0,0.5 L1,0.5" />
		</svg>
	</button>

	<div class="counter-viewport">
		<div class="counter-digits" style="transform: translate(0, {100 * offset}%)">
			<strong class="hidden" aria-hidden="true">{Math.floor($displayed_count + 1)}</strong>
			<strong>{Math.floor($displayed_count)}</strong>
		</div>
	</div>

	<button on:click={() => (count += 1)} aria-label="Increase the counter by one">
		<svg aria-hidden="true" viewBox="0 0 1 1">
			<path d="M0,0.5 L1,0.5 M0.5,0 L0.5,1" />
		</svg>
	</button> -->
</section>

<style>
	.control {
		display: flex;
		gap: 4px;
	}
	.control .dot {
		width: 10px;
		height: 10px;
		background: white;
		border-radius: 100px;
	}
	.control .active {
		width: 25px;
	}

	.slider-wrap {
		max-width: 1200px;
		margin: auto;
	}
	.higlight {
		color: var(--color-theme-1);
	}
	.slider {
		background: black;
		color: var(--color-theme-3);
		display: flex;
		align-items: center;

		padding: 10px 40px 10px 40px;
		border-radius: 30px;
	}
	.slider img {
		object-fit: contain;
		width: 50%;
	}
	.slider h2 {
		font-size: 2rem;
		max-width: 674px;
		line-height: 2.8rem;
	}
	/* .counter {
		display: flex;
		border-top: 1px solid rgba(0, 0, 0, 0.1);
		border-bottom: 1px solid rgba(0, 0, 0, 0.1);
		margin: 1rem 0;
	} */
</style>
