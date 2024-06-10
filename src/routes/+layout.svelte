<script>
	import Header from './Header.svelte';
	import './styles.css';
</script>

<div class="app">
	<Header />

	<main>
		<slot />
	</main>

	<footer>
		<div class="container">
			<address>
				<h3>IsyanaMerch</h3>
				<p>Contact Us</p>
				<p>
					<a href="mailto:kewoooooy@com">kewoooooy@com</a>
				</p>
				<p>
					<a href="tel:+1-555-555-5555">+1-555-555-5555</a>
				</p>
			</address>
		</div>
	</footer>
</div>

<style>
	address {
		font-style: normal;
		display: flex;
		flex-direction: column;
		gap: 10px;
	}
	.container {
		max-width: 1200px;
		margin: auto;
		padding: 100px 0 100px 0;
	}
	footer {
		background: var(--color-bg-2);
		margin-top: 100px;
	}
</style>
