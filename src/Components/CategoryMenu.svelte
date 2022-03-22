<script>
    import { onMount } from "svelte";
    import axios from "axios";
  
    //const endpoint = "https://api.allnigerianewspapers.com.ng/api/news";
    const endpoint = 'https://api.allnigerianewspapers.com.ng/api/category';
    let categorys = [];
  
    
  
    onMount(async function () {
        try {
          const response = await axios.get(endpoint);
          console.log(response.data);
          categorys = response.data;
        } catch (error) {
          console.error(error);
        }
    });
  
   
  </script>
  
  <main>
    <h1>Hello All NigeriaNews Paper Category!</h1>
  
    {#each categorys as c (c.id)}
      <div>
        <p>{c.name}</p>
      </div>
    {/each}
  </main>
  
  <style>
    /* ommitted for brevity */
  </style>