<script>
	let { data } = $props();
</script>

<h1>Create a New Event</h1>

<form method="POST" action="?/createEvent">
	<label for="title">Title</label>
	<input type="text" placeholder="Title" name="title" required />

	<label for="description">Description</label>
	<textarea placeholder="Description" name="description" required></textarea>

	<label for="url">URL</label>
	<input type="url" placeholder="URL" name="url" required />

	<label for="startDate">Start Date</label>
	<input type="date" name="startDate" required />	

	<label for="endDate">End Date</label>
	<input type="date" name="endDate" required />	

	<label for="startTime">Time</label>
	<input type="time" name="startTime" required />

	<label for="location">Location</label>
	<select name="locationId" required>
		{#each data.locations as location (location.id)}
		<option value="{location.id}">{location.name}</option>
		{/each}
	</select>

	<label for="category">Category</label>
	<select name="categoryId" required>
		{#each data.categories as category (category.id)}
		<option value="{category.id}">{category.name}</option>
		{/each}
	</select>

	<button type="submit" class="submit-button">Create Event</button>
</form>

<style>
	

	* {
		font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
		background-color: #f4f4f9;
		color: #333;
		margin: 0;
		padding: 20px;
		box-sizing: border-box;
	}

	h1 {
		text-align: center;
		color: #4A90E2;
		margin-bottom: 30px;
	}

	form {
		display: flex;
		flex-direction: column;
		max-width: 600px;
		margin: 0 auto;
		background-color: white;
		padding: 20px;
		border-radius: 8px;
		box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
	}

	label {
		margin-bottom: 5px;
		font-weight: bold;
	}

	input[type="text"],
	input[type="url"],
	input[type="date"],
	input[type="time"],
	textarea,
	select {
		padding: 12px;
		margin-bottom: 15px;
		border: 1px solid #ccc;
		border-radius: 5px;
		font-size: 16px;
		transition: border-color 0.3s;
	}

	input[type="text"]:focus,
	input[type="url"]:focus,
	input[type="date"]:focus,
	input[type="time"]:focus,
	textarea:focus,
	select:focus {
		border-color: #4A90E2;
		outline: none;
	}

	textarea {
		resize: vertical;
	}

	.submit-button {
		background: linear-gradient(90deg, #007BFF, #00A3E0);
		color: white;
		border: none;
		padding: 12px 20px;
		border-radius: 5px;
		cursor: pointer;
		transition: background 0.3s ease, transform 0.2s ease;
	}

	.submit-button:hover {
		background: linear-gradient(90deg, #0056b3, #007BFF);
		transform: scale(1.05);
	}
</style>