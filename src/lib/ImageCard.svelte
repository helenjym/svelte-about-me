<!-- src/lib/ImageCard.svelte -->

<script>
  export let image;  // Image URL prop
  export let title;  // Title prop
  export let description;  // Description prop
  export let imgAlt;
  export let imgDesc;
</script>

<style>
  .card {
    background-color: #d07586;
    border: 1px solid #e97f92;
    border-radius: 10px;
    overflow: hidden;
    width: 300px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    margin: 20px;
    text-align: center;
  }

  .card img {
    width: 250px;
    height: 250px;
    object-fit: cover;

  }

  .card-content {
    padding: 15px;
  }

  .card-title {
    font-size: 1.5em;
    color: #ffffff;
    margin: 0 0 10px 0;
  }

  .card-description {
    font-size: 1em;
    color: #ffffff;
    margin: 0;
  }

  .image-description{
    font-size: 12px;
    color: #ffffff;
    width: 250px;
    padding-left: 25px;
    padding-right: 25px;
    padding-bottom: 10px;
    font-style: italic;

  }
</style>

<div class="card">
  <img src={image} alt={imgAlt} />
  <p class="image-description">{imgDesc}</p>
  <div class="card-content">
    <h2 class="card-title">{title}</h2>
    <p class="card-description">{@html description}</p>
  </div>
</div>
