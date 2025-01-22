<script>
      import { enhance } from "$app/forms";
      import Warning from "$lib/components/Warning.svelte";
        export let form;
    </script>
    
    <div>
    
    
        <form action="?/login" method="POST" use:enhance>
    
            <label for="eamil">E-Mail</label>
            <input type="text" name="email" id="email" required>
    
            <label for="password">Password</label>
            <input type="password" name="password" id="password" required>
    
            <button type="submit">Login</button>
    
            {#if form}
    
            <Warning message={form.message} />
    
            {/if}
    
    
        </form>
    
    
    
    
    </div>
    
    
    <style>
        div {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f9f9f9;
            padding: 20px;
        }
    
        form {
            background-color: #ffffff;
            padding: 20px 30px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            display: flex;
            flex-direction: column;
            gap: 15px;
            width: 100%;
            max-width: 400px;
        }
    
        label {
            font-weight: 600;
            font-size: 14px;
            color: #333333;
        }
    
        input {
            padding: 10px;
            font-size: 14px;
            border: 1px solid #cccccc;
            border-radius: 5px;
            outline: none;
            transition: border-color 0.3s ease-in-out;
        }
    
        input:focus {
            border-color: #0077ff;
            box-shadow: 0 0 4px rgba(0, 119, 255, 0.5);
        }
    
        button {
            padding: 12px;
            font-size: 16px;
            font-weight: bold;
            color: #ffffff;
            background-color: #0077ff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease-in-out;
        }
    
        button:hover {
            background-color: #0056cc;
        }
    
        button:active {
            background-color: #003d99;
        }
    
       
    </style>
    