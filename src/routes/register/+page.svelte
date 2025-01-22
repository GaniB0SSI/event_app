<script>
      import { enhance } from '$app/forms';
      import Warning from '$lib/components/Warning.svelte';
      export let form;
    </script>
    
    <div>
    
      <form action="?/register" method="POST" use:enhance>
        <h1>Register</h1>
    
        <label for="email">E-Mail</label>
        <input type="text" name="email" id="email" required />
    
        <label for="username">Username</label>
        <input type="text" name="username" id="username" required />
    
        <label for="password">Password</label>
        <input type="password" name="password" id="password" required />
    
        <button type="submit">Register</button>
    
        {#if form}
          <Warning message={form.message} />
        {/if}
      </form>
    </div>
    <style>
    * {
        font-family: Arial, sans-serif;
        background: linear-gradient(135deg, #74ebd5, #acb6e5);
        margin: 0;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        color: #333;
    }
    
    div {
        background: #ffffff;
        padding: 2rem;
        border-radius: 10px;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        max-width: 400px;
        width: 100%;
    }
    
    h1 {
        font-size: 2rem;
        color: #333;
        text-align: center;
        margin-bottom: 1.5rem;
    }
    
    label {
        display: block;
        margin: 0.5rem 0 0.25rem;
        font-weight: bold;
    }
    
    input {
        width: 100%;
        padding: 0.75rem;
        margin-bottom: 1rem;
        border: 1px solid #ccc;
        border-radius: 5px;
        font-size: 1rem;
        transition: border-color 0.3s ease;
    }
    
    input:focus {
        border-color: #74ebd5;
        outline: none;
        box-shadow: 0 0 4px rgba(116, 235, 213, 0.5);
    }
    
    button {
        width: 100%;
        padding: 0.75rem;
        background: linear-gradient(135deg, #74ebd5, #acb6e5);
        border: none;
        border-radius: 5px;
        color: #fff;
        font-size: 1rem;
        font-weight: bold;
        cursor: pointer;
        transition: background 0.3s ease;
    }
    
    button:hover {
        background: linear-gradient(135deg, #acb6e5, #74ebd5);
    }
    
    </style>