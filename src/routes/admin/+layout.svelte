<script>
	export let children;
</script>

<nav>
	<a href="/admin/events">Events</a>
	<a href="/admin/locations">Locations</a>
	<a href="/admin/category">Category</a>
</nav>

{@render children()}
<style>
	:global(body) {
		font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
		background-color: #f9f9f9;
		margin: 0;
		padding: 0;
		color: #333;
	}

	nav {
		display: flex;
		justify-content: center;
		gap: 30px;
		background: linear-gradient(90deg, #007BFF, #00A3E0);
		padding: 15px 0;
		box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
		border-radius: 0 0 8px 8px;
	}

	nav a {
		color: #fff;
		text-decoration: none;
		font-size: 18px;
		position: relative;
		transition: color 0.3s;
	}

	nav a::after {
		content: '';
		display: block;
		width: 0;
		height: 2px;
		background: #cce7ff;
		transition: width 0.3s;
		position: absolute;
		bottom: -5px;
		left: 50%;
	}

	nav a:hover {
		color: #cce7ff;
	}

	nav a:hover::after {
		width: 100%;
		left: 0;
	}

	:global(main) {
		padding: 20px;
		max-width: 800px;
		margin: 20px auto;
		background: #fff;
		border-radius: 8px;
		box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
	}
</style>