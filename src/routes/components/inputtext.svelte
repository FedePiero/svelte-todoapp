<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();
  let value;

  function modifiedValue() {
    dispatch("modValue", {
      value: value,
    });
  }
</script>

<div class="flex items-center justify-center gap-12">
  <input placeholder="title" bind:value />
  <button on:click={modifiedValue}>Save it!</button>
</div>

<style>
  input {
    color: #333;
    font-size: 0.8rem;
    margin: 0 auto;
    padding: 0.1rem 0.3rem;
    border-radius: 0.3rem;
    background-color: rgb(255, 255, 255);
    border: none;
    width: 10rem;
    height: 2.5rem;
    display: block;
    border-bottom: 0.3rem solid transparent;
    transition: all 0.3s;
  }
  button {
    background: hsl(210, 98%, 80%);
    border: none;
    border-radius: 0.3rem;
    cursor: pointer;
    color: black;
    font-size: 0.8rem;
    width: 10rem;
    height: 2.5rem;
    padding: 0.1rem 0.3rem;
    overflow: hidden;
    position: relative;
    text-transform: lowercase;
  }
</style>
