<script lang="ts">
  import axios from "axios";
  import { onMount } from "svelte";

  let text = "";
  let images: {
    id: string;
    alt_description: string;
    urls: {
      regular: string;
    };
  }[] = [];

  const fetchData = async () => {
    const accessKey = import.meta.env.VITE_ACCESS_KEY;
    const response = await axios.get(`https://api.unsplash.com/search/photos?query=${text || "nature"}&client_id=${accessKey}`);

    images = response.data.results;
  };

  onMount(() => {
    fetchData();
  });

  const search = async () => {
    if (!text) return;
    await fetchData();
    text = "";
  };
</script>

<div class="container">
  <div class="header">
    <h1>Image Gallery</h1>
    <div class="search-bar">
      <input type="text" placeholder="Search" bind:value={text} />
      <button on:click={search}>Search</button>
    </div>
  </div>
  <div class="images">
    {#each images as image}
      <div class="image">
        <img src={image.urls.regular} alt={image.alt_description} class="image" />
      </div>
    {/each}
  </div>
</div>

<style>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .header {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 20px;
  }

  .search-bar {
    display: flex;
    margin-top: 20px;
  }

  input {
    padding: 10px;
    border-radius: 5px;
    border: 1px solid #ccc;
  }

  button {
    padding: 10px;
    border-radius: 5px;
    border: 1px solid #ccc;
    margin-left: 10px;
  }

  .images {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin-top: 20px;
  }

  .image {
    width: 400px;
    margin: 10px;
  }
</style>
