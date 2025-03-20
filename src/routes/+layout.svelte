<script>
	import { onMount } from 'svelte';

	let isMenuOpen = false;

	function toggleMenu() {
		isMenuOpen = !isMenuOpen;
	}

	onMount(() => {
		// Add a class to the body when the app is mounted
		document.body.classList.add('mobile-app');
	});
</script>

<svelte:head>
	<title>Yoga App</title>
	<meta
		name="viewport"
		content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no"
	/>
	<meta name="theme-color" content="#6B46C1" />
	<link
		href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600&display=swap"
		rel="stylesheet"
	/>
</svelte:head>

<div class="app-container">
	<header class="app-header">
		<div class="logo">Yoga App</div>
		<button class="menu-button" on:click={toggleMenu} aria-label="Menu">
			<span></span>
			<span></span>
			<span></span>
		</button>
	</header>

	<nav class="main-nav" class:open={isMenuOpen}>
		<ul>
			<li><a href="/" on:click={() => (isMenuOpen = false)}>Home</a></li>
			<!-- <li><a href="/favorites" on:click={() => (isMenuOpen = false)}>Favorites</a></li>
			<li><a href="/categories" on:click={() => (isMenuOpen = false)}>Categories</a></li>
			<li><a href="/about" on:click={() => (isMenuOpen = false)}>About</a></li> -->
		</ul>
	</nav>

	<main class="app-content">
		<slot />
	</main>

	<footer class="app-footer">
		<p>© {new Date().getFullYear()} Yoga App</p>
	</footer>
</div>

<style>
	:global(body) {
		margin: 0;
		padding: 0;
		font-family:
			'Poppins',
			-apple-system,
			BlinkMacSystemFont,
			sans-serif;
		background-color: #f8f9fa;
		color: #333;
		overflow-x: hidden;
		position: relative;
		min-height: 100vh;
	}

	:global(body.mobile-app) {
		-webkit-tap-highlight-color: transparent;
		-webkit-touch-callout: none;
		-webkit-user-select: none;
		user-select: none;
	}

	.app-container {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

	.app-header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 0.8rem 1rem;
		background: linear-gradient(to right, #6b46c1, #9f7aea);
		color: white;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
		position: sticky;
		top: 0;
		z-index: 100;
		padding-top: 40px;
	}

	.logo {
		font-size: 1.5rem;
		font-weight: 600;
	}

	.menu-button {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		width: 24px;
		height: 18px;
		background: transparent;
		border: none;
		cursor: pointer;
		padding: 0;
	}

	.menu-button span {
		display: block;
		height: 2px;
		width: 100%;
		background-color: white;
		border-radius: 2px;
		transition: all 0.2s ease;
	}

	.main-nav {
		position: fixed;
		top: 0;
		right: 0;
		height: 100vh;
		width: 75%;
		max-width: 300px;
		background-color: white;
		z-index: 200;
		transform: translateX(100%);
		transition: transform 0.3s ease;
		box-shadow: -2px 0 5px rgba(0, 0, 0, 0.1);
		padding-top: 60px;
	}

	.main-nav.open {
		transform: translateX(0);
	}

	.main-nav ul {
		list-style: none;
		padding: 0;
		margin: 0;
	}

	.main-nav li {
		border-bottom: 1px solid #eee;
	}

	.main-nav a {
		display: block;
		padding: 1rem 1.5rem;
		color: #333;
		text-decoration: none;
		font-size: 1.1rem;
		transition: background-color 0.2s;
	}

	.main-nav a:hover,
	.main-nav a:focus {
		background-color: #f2f2f2;
	}

	.app-content {
		flex: 1;
		padding: 1rem;
		width: 100%;
		box-sizing: border-box;
		max-width: 100%;
		margin: 0 auto;
	}

	.app-footer {
		text-align: center;
		padding: 1rem;
		background-color: #f1f1f1;
		font-size: 0.9rem;
		color: #666;
	}

	@media (min-width: 768px) {
		.app-content {
			padding: 1.5rem;
			max-width: 800px;
		}
	}
</style>
