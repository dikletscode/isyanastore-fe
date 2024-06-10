<script>
	import Category from './Category.svelte';
	import Products from './Products.svelte';
	import Slider from './Slider.svelte';
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<Slider />
	<Products />
	<Category />
</section>

<style>
</style>
