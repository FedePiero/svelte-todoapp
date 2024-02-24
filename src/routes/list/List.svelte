<script>
  import { onMount } from "svelte";
  import { onDestroy } from "svelte";
  import Checkbox from "../components/checkbox.svelte";
  import { browser } from "$app/environment";
  import Inputtext from "../components/inputtext.svelte";

  let toDoList = [];

  onMount(() => {
    if (browser) {
      const itemsSessionStorage = window.sessionStorage.getItem("toDoList");
      if (
        itemsSessionStorage === null ||
        JSON.parse(itemsSessionStorage).length === 0
      ) {
        toDoList = [
          {
            title: "buy the car",
            done: false,
          },
          {
            title: "2000 profit",
            done: false,
          },
          {
            title: "read 20 books",
            done: true,
          },
        ];
      } else {
        toDoList = JSON.parse(itemsSessionStorage);
      }
    }
  });

  onDestroy(() => {
    if (browser) {
      window.sessionStorage.setItem("toDoList", JSON.stringify(toDoList));
    }
  });

  function handleCheckBox(event) {
    toDoList.filter((o) => o.title === event.detail.item.title)[0].done =
      event.detail.item.done;
  }
  function handleInputText(event) {
    if (event.detail.value === undefined) return;
    toDoList.push({
      title: event.detail.value,
      done: false,
    });
    toDoList = toDoList;
  }
  function findIndex(item) {
    for (let i = 0; i < toDoList.length; i++) {
      if (item.title === toDoList[i].title) return i;
    }
    return -1;
  }
  function removeElement(item) {
    const index = findIndex(item);
    if (index >= 0) {
      toDoList.splice(index, 1);
    }
    toDoList = toDoList;
  }
</script>

<div class="text-3xl font-bold flex items-center justify-center">
  <div class="w-screen h-screen">
    <h1 class="flex items-center justify-center m-12 pb-5">This is your To Do List:</h1>
    <div class="pb-8">
      {#each toDoList as item}
        <div class="m-10 rounded-md flex justify-center gap-12">
          <button on:click={() => removeElement(item)}>Remove</button>
          <span>
            {item.title}
          </span>
          <Checkbox {item} on:modValue={handleCheckBox}></Checkbox>
        </div>
      {/each}
    </div>
    <div class="verticalLine"></div>
    <div class="m-10 rounded-md flex justify-center gap-12 m-12 pt-8">
      <span>Add New One:</span>
      <Inputtext on:modValue={handleInputText}></Inputtext>
    </div>
  </div>
</div>

<style>
  button {
    background: hsl(0, 98%, 80%);
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
  span {
    font-size: 1.0rem;
  }
  .verticalLine {
    border: 1px solid rgb(255, 255, 255);
    width: 60%;
    margin: 0 20%;
  }
</style>
