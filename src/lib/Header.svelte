<script>
  import FaExpandArrowsAlt from "svelte-icons/fa/FaExpandArrowsAlt.svelte";
  import FaCompressArrowsAlt from "svelte-icons/fa/FaCompressArrowsAlt.svelte";
  import FaRegWindowClose from "svelte-icons/fa/FaRegWindowClose.svelte";
  import FaRegCheckSquare from "svelte-icons/fa/FaRegCheckSquare.svelte";
  import FaRegStickyNote from "svelte-icons/fa/FaRegStickyNote.svelte";
  import FaPlus from "svelte-icons/fa/FaPlus.svelte";

  export let handleOnActiveTabChange;
  export let setShowHome;
  export let handleOnMaximizeHome;

  let activeTab = "notes";
  let isHomeMaxed = false;
</script>

<div
  class="flex flex-row text-center"
  on:dblclick={() => {
    isHomeMaxed = !isHomeMaxed;
    handleOnMaximizeHome(isHomeMaxed);
  }}
>
  <div
    class={`basis-2/6 inline-flex rounded-md menuItemContainer cursorPointer ${
      activeTab === "notes" ? "active" : ""
    }`}
    on:click={() => {
      activeTab = "notes";
      handleOnActiveTabChange("notes");
    }}
  >
    <div class="w-5"><FaRegStickyNote /></div>
    <span class="ml-2">Notes</span>
  </div>
  <div
    class={`basis-2/6 ml-2.5 inline-flex rounded-md menuItemContainer cursorPointer ${
      activeTab === "todos" ? "active" : ""
    }`}
    on:click={() => {
      activeTab = "todos";
      handleOnActiveTabChange("todos");
    }}
  >
    <div class="w-5"><FaRegCheckSquare /></div>
    <span class="ml-2">TODOs</span>
  </div>
  <div class="basis-1/6 inline-flex" />
  <div class="basis-1/6 inline-flex justify-end">
    <div
      class="w-4 float-right self-center glowOnHover cursorPointer"
      on:click={() => {
        isHomeMaxed = !isHomeMaxed;
        handleOnMaximizeHome(isHomeMaxed);
      }}
    >
      <FaExpandArrowsAlt />
    </div>
    <div
      class="fixedHeight ml-4 rotate-45	 float-right self-center glowOnHover cursorPointer"
      on:click={() => setShowHome(false)}
    >
      <FaPlus />
    </div>
  </div>
</div>

<style>
  .menuItemContainer {
    border: 1px solid aliceblue;
    align-items: center;
    justify-content: center;
  }

  .menuItemContainer:hover {
    background-color: aliceblue;
    backdrop-filter: blur(8px);
  }

  .cursorPointer:hover {
    cursor: pointer;
  }

  .active {
    background-color: aliceblue;
    backdrop-filter: blur(8px);
  }

  .glowOnHover:hover {
    color: aliceblue;
  }

  .fixedHeight {
    height: 1.45rem;
  }
</style>
