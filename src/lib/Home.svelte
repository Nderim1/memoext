<script>
  import { slide } from "svelte/transition";
  import Header from "./Header.svelte";
  import NotesHome from "./Notes/index.svelte";
  import TodosHome from "./Todos/index.svelte";
  // import {slide} from 'svelte/transition'

  export let setShowHome;

  let activeTab = "todos";
  let maximizeHome = false;

  const handleOnActiveTabChange = (tab) => {
    activeTab = tab;
    console.log("hello tab", tab);
  };

  const handleOnMaximizeHome = (max) => {
    maximizeHome = max;
  };
</script>

<div
  transition:slide={{ duration: 200 }}
  class={`h-80 w-80 fixed bottom-3 right-3 rounded-md p-3 blurThis ${
    maximizeHome ? "maximizeHome" : ""
  }`}
>
  <Header {handleOnActiveTabChange} {setShowHome} {handleOnMaximizeHome} />
  <hr class="mt-3 border-1 border-blue-50" />
  <div class="p-5 h-5/6 overflow-scroll">
    {#if activeTab === "notes"}
      <NotesHome />
    {:else if activeTab === "todos"}
      <TodosHome />
    {/if}
  </div>
</div>

<style>
  div {
    color: rgb(25, 25, 25);
  }
  .blurThis {
    backdrop-filter: blur(8px);
    background-color: rgba(255, 255, 255, 0.3);
  }

  .maximizeHome {
    width: 600px;
    height: 600px;
  }
</style>
