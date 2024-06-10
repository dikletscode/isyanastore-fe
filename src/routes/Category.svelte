<script>
	import { spring } from 'svelte/motion';
	import logo from '$lib/images/08.webp';

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

<section class="categories">
	<h2>Categories</h2>
	<ul class="cards">
		<li class="card">
			<div class="thumbnail">
				<img src={logo} alt="" height="150" width="150" />
			</div>
			<div class="description">
				<p>Album</p>
			</div>
		</li>
		<li class="card">
			<div class="thumbnail">
				<img src={logo} alt="" height="150" width="150" />
			</div>
			<div class="description">
				<p>Merch</p>
			</div>
		</li>
		<li class="card">
			<div class="thumbnail">
				<img src={logo} alt="" height="150" width="150" />
			</div>
			<div class="description">
				<p>Explore!</p>
			</div>
		</li>
		<li class="card">
			<div class="thumbnail">
				<img src={logo} alt="" height="150" width="150" />
			</div>
			<div class="description">
				<p>Explore!</p>
			</div>
		</li>
		<li class="card">
			<div class="thumbnail">
				<img src={logo} alt="" height="150" width="150" />
			</div>
			<div class="description">
				<p>Explore!</p>
			</div>
		</li>
	</ul>
</section>

<style>
	.cards {
		list-style: none;
		padding-top: 30px;
		display: grid;
		grid-template-columns: repeat(5, 1fr);
	}

	.categories {
		max-width: 1200px;
		padding: 80px 0 0 0;
		color: var(--color-theme-2);
		margin: auto;
	}
	.card {
		border-radius: 20px;
		width: 150px;
	}
	.thumbnail {
		border: 0.5px solid var(--color-theme-1);
		width: 150px;
		height: 150px;
		background: whitesmoke;
		border-radius: 100%;
	}

	.description {
		font-size: 1rem;
		padding-top: 20px;
		text-align: center;
		font-weight: 500;
	}
</style>
