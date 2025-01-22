<script>
	import { flip } from 'svelte/animate';

	let { data } = $props();
	let filteredEvents = $state(data.events);
	let selectedCategory = $state('all');

	function filterEvents() {
		if (selectedCategory === 'all') {
			filteredEvents = data.events;
		} else {
			filteredEvents = data.events.filter((e) => e.category_id === selectedCategory.id);
		}
	}
</script>

<div>
	{#if data.user}
	<p>Welcome back {data.user.username}</p>
	<form action="/logout?/logout" method="POST">
	<button type="submit">Logout</button>
    </form>


<form action="/logout?/deleteAccount" method="POST">
    <button type="submit">Delete Account</button>
</form>

	{:else}

	<p>
		You are not logged in.
	</p>
	<p>
		<a href="/login">Login</a>
		or
		<a href="/register">Register</a>
	</p>
	{/if}
</div>

<div class="container">
	<h1>🌟 My Event App 🌟</h1>

	<p>Explore the latest events happening now!</p>

	<div class="filter-section">
		<label for="category">Filter by Category:</label>
		<select id="category" bind:value={selectedCategory} onchange={filterEvents}>
			<option value="all">All</option>
			{#each data.categories as category}
				<option value="{category}">{category.name}</option>
			{/each}
		</select>
	</div>

	<div class="events-list">
		{#each filteredEvents as event (event.id)}
			<div class="event-card" animate:flip>
				<h2>{event.title}</h2>
				<p>Date: {event.start_date}</p>
				<p>Category: {event.category_id}</p>
			</div>
		{/each}
	</div>
</div>

<style>
	/* Container Styling */
	.container {
		font-family: 'Arial', sans-serif;
		padding: 20px;
		max-width: 800px;
		margin: auto;
		text-align: center;
		color: #333;
		background-color: #f9f9f9;
		border-radius: 10px;
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
	}

	/* Header Styling */
	h1 {
		font-size: 2rem;
		color: #007BFF;
		margin-bottom: 10px;
	}

	/* Paragraph Styling */
	p {
		font-size: 1.1rem;
		color: #555;
		margin-bottom: 20px;
	}

	/* Filter Section Styling */
	.filter-section {
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 10px;
		margin-bottom: 20px;
	}

	label {
		font-size: 1rem;
		font-weight: bold;
		color: #555;
	}

	select {
		padding: 10px;
		border-radius: 5px;
		border: 1px solid #ccc;
		font-size: 1rem;
		color: #555;
		background-color: #fff;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
		cursor: pointer;
		transition: border-color 0.3s;
	}

	select:hover,
	select:focus {
		border-color: #007BFF;
		outline: none;
	}

	/* Events List Styling */
	.events-list {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		gap: 20px;
	}

	.event-card {
		background-color: #fff;
		border: 1px solid #eee;
		border-radius: 10px;
		padding: 15px;
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
		transition: transform 0.3s, box-shadow 0.3s;
		text-align: left;
	}

	.event-card:hover {
		transform: translateY(-5px);
		box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
	}

	.event-card h2 {
		font-size: 1.5rem;
		color: #007BFF;
		margin-bottom: 10px;
	}

	.event-card p {
		font-size: 1rem;
		color: #666;
		margin: 5px 0;
	}
	
</style>
