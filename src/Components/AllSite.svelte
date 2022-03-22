<script>
    import { onMount } from "svelte";
    import axios from "axios";
  
    const endpoint = "http://api.allnigerianewspapers.com.ng/api/site/";
  
  
    let sites = [];
  
    
  
    onMount(async function () {
        try {
          const response = await axios.get(endpoint);
          console.log(response.data);
          sites = response.data;
        } catch (error) {
          console.error(error);
        }
    });
  
   
  </script>
  
  <main>
    {#await sites}
        <p>wait...</p>
    {:then sites}
        <p>The Site List are:</p>
{#if sites}
        {#each sites as site}
            <li>
                {site.name}
            </li>
        {/each}
{/if}
    {:catch error}
        <p style="color: red">{error}</p>
    {/await}
</main>

  <style>
    /* ommitted for brevity */
  </style>