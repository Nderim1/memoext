<script>
  export let todoToDisplay;
  export let onCheckboxCheck;
  export let key;
  export let handleOnEditTodo;
  export let removeTodo;

  import FaPencilAlt from "svelte-icons/fa/FaPencilAlt.svelte";
  import FaTrashAlt from "svelte-icons/fa/FaTrashAlt.svelte";
  import FaCheck from "svelte-icons/fa/FaCheck.svelte";

  let editMode = false;
  const today = new Date();
  let isTodoDone = todoToDisplay.status === "done";
  let dateAndTime = today.toLocaleString();

  const onFakeCheckboxClick = () => {
    isTodoDone = todoToDisplay.status !== "done";
    let status = isTodoDone ? "done" : "todo";
    onCheckboxCheck(status);
    updateTimeAndDate();
    isTodoDone = false;
  };

  const updateTimeAndDate = () => {
    dateAndTime = new Date().toLocaleString();
  };
</script>

<div class="flex rounded-sm items-center pb-2">
  <div
    class="h-5 w-5 minWidth mr-2 cursor-pointer border-2 border-black rounded-sm"
    on:click={onFakeCheckboxClick}
  >
    {#if todoToDisplay.status === "done"}
      <div><FaCheck /></div>
    {/if}
  </div>
  <!-- <span id="dateAndTime">{dateAndTime}</span> -->
  <!-- {#if editMode}
    <input id="editInput" bind:value={todoToDisplay.title} />
    {/if}
    {:else} -->
  <span
    class={`${todoToDisplay.status} cursor-pointer text-ellipsis overflow-hidden whitespace-nowrap`}
    on:click={onFakeCheckboxClick}>{todoToDisplay.title}</span
  >
  <div class="ml-auto inline-flex">
    <div
      class=" h-4 w-4 cursor-pointer ml-4 hover:text-blue-50"
      on:click={handleOnEditTodo}
    >
      <FaPencilAlt />
    </div>
    <div
      class=" h-4 w-4 cursor-pointer ml-4 hover:text-blue-50"
      on:click={removeTodo}
    >
      <FaTrashAlt />
    </div>
  </div>
</div>

<style>
  .done {
    text-decoration: line-through;
  }

  .minWidth {
    min-width: 20px;
  }
</style>
