<script></script>

<div class="container">
  <div class="header">
    <h1>Image Gallery</h1>
    <div class="search-bar">
      <input type="text" placeholder="Search" />
      <button>Search</button>
    </div>
  </div>
  <div class="images">
    <img src="" alt="" class="image" />
    <img src="" alt="" class="image" />
    <img src="" alt="" class="image" />
    <img src="" alt="" class="image" />
    <img src="" alt="" class="image" />
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
    height: 200px;
    margin: 10px;
  }
</style>
