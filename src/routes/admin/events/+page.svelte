<script>
	import { enhance } from '$app/forms';
	import { slide } from 'svelte/transition';
	let { data } = $props();
</script>

<h1>Admin Dashboard</h1>
<a href="/admin/events/new" class="create-button">Create a New Event</a>
{#each data.events as event (event.id)}
	<div class="box" transition:slide>
		<p class="event-info">{event.id} - {event.title} - {event.locationName}</p>

		<form action="?/deleteEvent" method="POST" use:enhance class="delete-form">
			<input type="hidden" name="id" value={event.id} />
			<button type="submit" class="delete-button">Delete</button>
		</form>
	</div>
{/each}

<style>
	* {
		box-sizing: border-box;
		font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
		background-color: #f4f4f9;
		color: #333;
		margin: 0;
		padding: 20px;
	}

	
	h1 {
		text-align: center;
		color: #4A90E2;
		margin-bottom: 30px;
	}

	.create-button {
		display: flex;
		justify-content: center;
		background: linear-gradient(90deg, #007BFF, #00A3E0);
		color: white;
		padding: 12px 20px;
		text-decoration: none;
		border-radius: 5px;
		margin-bottom: 20px;
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
		transition: background 0.3s ease, box-shadow 0.3s ease;
	}

	.create-button:hover {
		background: linear-gradient(90deg, #0056b3, #007BFF);
		box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15);
	}

	.box {
		background-color: white;
		border: 1px solid #e0e0e0;
		border-radius: 8px;
		padding: 20px;
		margin: 15px 0;
		box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
		transition: transform 0.2s, box-shadow 0.2s;
	}

	.box:hover {
		transform: translateY(-3px);
		box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
	}

	.event-info {
		margin: 0;
		font-size: 16px;
		color: #333;
	}

	.delete-form {
		margin-top: 10px;
	}

	.delete-button {
		background-color: #dc3545;
		color: white;
		border: none;
		padding: 10px 15px;
		border-radius: 5px;
		cursor: pointer;
		transition: background-color 0.3s, transform 0.2s;
	}

	.delete-button:hover {
		background-color: #c82333;
		transform: scale(1.05);
	}
</style>