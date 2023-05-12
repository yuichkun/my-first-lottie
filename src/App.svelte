<script lang="ts">
  import lottie from "lottie-web";
  import { onMount } from "svelte";
  let element: HTMLDivElement;

  onMount(() => {
    lottie.loadAnimation({
      container: element, // the dom element that will contain the animation
      renderer: "svg",
      loop: true,
      autoplay: true,
      path: "lottie.json", // the path to the animation json
    });
  });
</script>

<main>
  <h1>Vite + Svelte</h1>
  <div id="container" bind:this={element} />
</main>

<style>
  #container {
    /* min-width: 300px;
    min-height: 300px; */
    max-width: 100%;
    max-height: 100%;
    background-color: #1e1c26;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    margin: auto;
  }
</style>
