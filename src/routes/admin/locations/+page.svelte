<script>
    import { enhance } from '$app/forms';
    import { slide } from 'svelte/transition';
  
    let { data, form } = $props();
    console.log(data);
  </script>
  
  <h1>Locations</h1>
  <a href="/admin/locations/new" class="create-location-btn">+ Create New Location</a>
  
  {#if form && !form.success}
      <div class="warning">
          {form.message}
      </div>
  {/if}
  
  {#each data.locations as location (location.id)}
    <div class="box" transition:slide>
        <div class="content">
            <p class="location-title">{location.name}</p>
            <p class="location-description">Description: {location.description}</p>
        </div>
  
        <form action="?/deleteLocation" method="POST" use:enhance>
            <input type="hidden" name="id" value={location.id} />
            <button type="submit" class="delete-btn">Delete</button>
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
        font-size: 2.5rem;
        margin-bottom: 30px;
        color: #1a1a1a;
    }
  
    .create-location-btn {
        display: block;
        width: fit-content;
        margin: 0 auto 30px;
        padding: 12px 20px;
        background-color: #007BFF;
        color: white;
        text-decoration: none;
        font-size: 1rem;
        font-weight: 600;
        border-radius: 5px;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        transition: background-color 0.3s ease, box-shadow 0.3s ease;
    }
  
    .create-location-btn:hover {
        background-color: #0056b3;
        box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15);
    }
  
    .warning {
        background-color: #fff3cd;
        color: #856404;
        padding: 10px;
        border: 1px solid #ffeeba;
        border-radius: 5px;
        margin-bottom: 20px;
        text-align: center;
    }
  
    .box {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 20px;
        margin: 15px auto;
        width: 80%;
        background-color: white;
        border: 1px solid #e0e0e0;
        border-radius: 8px;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        transition: transform 0.2s ease, box-shadow 0.2s ease;
    }
  
    .box:hover {
        transform: translateY(-3px);
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12);
    }
  
    .content {
        display: flex;
        flex-direction: column;
        flex-grow: 1;
    }
  
    .location-title {
        font-size: 1.2rem;
        font-weight: 600;
        margin: 0;
        color: #333;
    }
  
    .location-description {
        font-size: 0.9rem;
        color: #666;
        margin-top: 5px;
    }
  
    .delete-btn {
        background-color: #dc3545;
        color: white;
        border: none;
        padding: 10px 15px;
        font-size: 0.9rem;
        font-weight: 600;
        border-radius: 5px;
        cursor: pointer;
        transition: background-color 0.3s ease;
    }
  
    .delete-btn:hover {
        background-color: #c82333;
    }
  </style>