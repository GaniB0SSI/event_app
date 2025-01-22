<script>
	let { data } = $props();
</script>

<h1>Create a New Category</h1>

<form method="POST" action="?/createCategory" use:enhance>
    <label for="name">Name</label>
    <textarea placeholder="Name" name="name" required></textarea>

    <button type="submit" class="submit-button">Create Category</button>
</form>

<style>
	form {
		display: flex;
		flex-direction: column;
		gap: 15px;
		background-color: #fff;
		padding: 20px;
		border-radius: 8px;
		box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
		max-width: 400px;
		width: 100%;
		margin: 0 auto; /* Center the form */
	}

	label {
		font-size: 14px;
		font-weight: bold;
		color: #555;
	}

	textarea {
		resize: none;
		padding: 10px;
		border: 1px solid #ccc;
		border-radius: 4px;
		font-size: 14px;
		min-height: 80px;
		box-sizing: border-box;
		transition: border-color 0.3s;
	}

	textarea:focus {
		border-color: #007BFF;
		outline: none;
	}

	.submit-button {
		padding: 10px 15px;
		background: linear-gradient(90deg, #007BFF, #00A3E0);
		color: #fff;
		border: none;
		border-radius: 4px;
		font-size: 16px;
		cursor: pointer;
		transition: background 0.3s, transform 0.2s;
	}

	.submit-button:hover {
		background: linear-gradient(90deg, #0056b3, #007BFF);
		transform: scale(1.05);
	}

	h1 {
		text-align: center;
		margin-bottom: 20px;
		font-size: 24px;
		color: #007BFF;
	}
</style>