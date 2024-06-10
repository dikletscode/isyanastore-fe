<script>
	import { spring } from 'svelte/motion';
	import logo from '$lib/images/1200x1200bf-60.jpg';
	/**
	 * Fetches and displays a single product's details.
	 *
	 * @component
	 */
	import { onMount } from 'svelte';
	import { writable } from 'svelte/store';

	/** @type {import('svelte/store').Writable<Product[]>} */
	export const products = writable([]);

	/**
	 * @typedef {Object} Product
	 * @property {number} id
	 * @property {string} name
	 * @property {string} description
	 * @property {number} price
	 */

	onMount(async () => {
		try {
			const response = await fetch('http://127.0.0.1:5000/product');
			if (!response.ok) {
				throw new Error('Network response was not ok.');
			}
			const data = await response.json();
			console.log(data, 'asep');
			products.set(data?.data);
		} catch (error) {
			console.error('Error ', error);
		}
	});
</script>

<section class="etalase">
	<h2>🎸 Unbeatable Value - Don't Miss Out!</h2>
	{#if $products != null}
		<ul class="cards">
			{#each $products as product, index}
				<li class="card">
					<div class="thumbnail">
						<img src={logo} alt="" height="250" width="250" />
					</div>
					<div class="description">
						<p>{product.name}</p>
						<p>Rp.{product.price}</p>
					</div>
				</li>
			{/each}

			<!-- <li class="card">
			<div class="thumbnail">
				<img src={logo} alt="" height="250" width="250" />
			</div>
			<div class="description">
				<p>Explore!</p>
				<p>Rp.400.000</p>
			</div>
		</li> -->
			<!-- <li class="card">
			<div class="thumbnail">
				<img src={logo} alt="" height="250" width="250" />
			</div>
			<div class="description">
				<p>Explore!</p>
				<p>Rp.400.000</p>
			</div>
		</li>
		<li class="card">
			<div class="thumbnail">
				<img src={logo} alt="" height="250" width="250" />
			</div>
			<div class="description">
				<p>Explore!</p>
				<p>Rp.400.000</p>
			</div>
		</li>
		<li class="card">
			<div class="thumbnail">
				<img src={logo} alt="" height="250" width="250" />
			</div>
			<div class="description">
				<p>Explore!</p>
				<p>Rp.400.000</p>
			</div>
		</li> -->
		</ul>
	{:else}
		<p>Loading product...</p>
	{/if}
</section>

<style>
	.cards {
		list-style: none;
		justify-content: space-between;
		display: grid;
		grid-template-columns: repeat(4, 1fr);
	}

	.etalase {
		max-width: 1200px;
		padding: 80px 0 0 0;
		color: var(--color-theme-2);
		margin: auto;
	}
	.card {
		border: 0.5px solid rgb(203, 199, 199);
		border-radius: 20px;
		width: 250px;
		overflow: hidden;
	}
	.card .description {
		padding: 8px 16px 8px 16px;
	}
	.description :nth-child(1) {
		font-size: 1rem;
		padding-bottom: 10px;
		font-weight: 500;
	}
	.description :nth-child(2) {
		font-size: 1rem;
		font-weight: 600;
		padding-bottom: 10px;
	}
	.etalase h2 {
		padding-bottom: 24px;
	}
</style>
