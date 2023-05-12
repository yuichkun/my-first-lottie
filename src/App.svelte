<script lang="ts">
  import lottie from "lottie-web";
  import { onMount } from "svelte";
  let element: HTMLDivElement;

  function render(jsonStr: string) {
    const animationData = JSON.parse(jsonStr);
    lottie.destroy();
    lottie.loadAnimation({
      container: element, // the dom element that will contain the animation
      renderer: "svg",
      loop: true,
      autoplay: true,
      animationData,
    });
  }

  onMount(() => {
    lottie.loadAnimation({
      container: element, // the dom element that will contain the animation
      renderer: "svg",
      loop: true,
      autoplay: true,
      path: "lottie.json", // the path to the animation json
    });
  });
  const onChange = (e: any) => {
    const [file] = e.target.files;
    if (!file) alert("specify file!!");
    const reader = new FileReader();
    reader.onload = function () {
      const lottieFile = reader.result;
      render(lottieFile as string);
    };
    reader.readAsText(file);
  };
</script>

<main>
  <div id="container" bind:this={element} />
  <input type="file" id="load" on:change={onChange} />
</main>

<style>
  #container {
    /* min-width: 300px;
    min-height: 300px; */
    max-width: 100%;
    max-height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    margin: auto;
  }
  #load {
    position: absolute;
    top: 0;
    left: 0;
    border: 1px solid white;
  }
</style>
