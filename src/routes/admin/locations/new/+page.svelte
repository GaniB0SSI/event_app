<script>
    import { enhance } from '$app/forms';
</script>

<h1>Create New Location</h1>
<form method="POST" action="?/createLocation" use:enhance>
    <label for="name">Name</label>
    <input type="text" placeholder="Name" name="name" required />

    <label for="description">Description</label>
    <textarea placeholder="Description" name="description" required></textarea>
    
    <button type="submit" class="submit-button">Create Location</button>
</form>

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
    textarea {
        padding: 12px;
        margin-bottom: 15px;
        border: 1px solid #ccc;
        border-radius: 5px;
        font-size: 16px;
        transition: border-color 0.3s;
    }

    input[type="text"]:focus,
    textarea:focus {
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