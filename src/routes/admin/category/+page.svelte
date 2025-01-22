<script>
	import { enhance } from '$app/forms';
	import { slide } from 'svelte/transition';
	import Warning from '$lib/components/Warning.svelte';
	let { data, form } = $props();
</script>

<div class="body">
	<h1>Categories</h1>
	<a class="create-link" href="/admin/category/new">+ Create New Category</a>

	{#if form && !form.success}
		<Warning message={form.message} />
	{/if}

	<div class="categories-list">
		{#each data.categories as category (category.id)}
			<div class="box" transition:slide>
				<p class="category-info">
					<span class="category-name">{category.name}</span>
					<span class="category-id">ID: {category.id}</span>
				</p>

				<form action="?/deleteCategory" method="POST" use:enhance>
					<input type="hidden" name="id" value={category.id} />
					<button type="submit" class="delete-button">Delete</button>
				</form>
			</div>
		{/each}
	</div>
</div>

<style>
	/* General Page Styling */
	.body {
		font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
		background-color: #f4f6f8;
		margin: 0;
		padding: 20px;
		color: #333;
		min-height: 100vh;
		box-sizing: border-box;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	h1 {
		color: #2c3e50;
		font-size: 32px;
		margin-bottom: 15px;
	}

	/* Create Category Link */
	.create-link {
		font-size: 16px;
		color: #ffffff;
		background: linear-gradient(90deg, #007BFF, #00A3E0);
		padding: 10px 15px;
		border-radius: 8px;
		text-decoration: none;
		margin-bottom: 20px;
		transition: background 0.3s, box-shadow 0.3s;
	}

	.create-link:hover {
		background: linear-gradient(90deg, #0056b3, #007BFF);
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
	}

	/* Category List Container */
	.categories-list {
		display: flex;
		flex-direction: column;
		width: 100%;
		max-width: 800px;
		gap: 15px;
	}

	/* Individual Category Box */
	.box {
		background: #ffffff;
		border-radius: 12px;
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
		padding: 15px 20px;
		display: flex;
		justify-content: space-between;
		align-items: center;
		transition: box-shadow 0.3s, transform 0.3s;
	}

	.box:hover {
		box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
		transform: translateY(-2px);
	}

	.category-info {
		display: flex;
		flex-direction: column;
		gap: 5px;
	}

	.category-name {
		font-weight: bold;
		color: #007bff;
		font-size: 18px;
	}

	.category-id {
		color: #6c757d;
		font-size: 14px;
	}

	/* Delete Button */
	.delete-button {
		background-color: #e74c3c;
		color: #ffffff;
		border: none;
		border-radius: 6px;
		padding: 8px 12px;
		font-size: 14px;
		cursor: pointer;
		transition: background-color 0.3s, box-shadow 0.3s;
	}

	.delete-button:hover {
		background-color: #c0392b;
		box-shadow: 0 2px 6px rgba(231, 76, 60, 0.4);
	}
</style>