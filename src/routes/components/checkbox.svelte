<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();
  export let item;

  function modifiedValue() {
    dispatch("modValue", {
      item: item,
    });
  }
</script>

<label>
  <input type="checkbox" on:click={modifiedValue} bind:checked={item.done} />
</label>
