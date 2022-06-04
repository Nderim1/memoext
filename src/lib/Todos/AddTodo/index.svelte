<script>
  import { beforeUpdate, afterUpdate } from "svelte";
  import FaPlus from "svelte-icons/fa/FaPlus.svelte";
  import FaPencilAlt from "svelte-icons/fa/FaPencilAlt.svelte";
  export let addTodo;
  export let todoToEdit;
  export let editTodo;
  $: todoToAdd = todoToEdit || "";

  const prepareAndAddTodo = (todo) => {
    if (todo.length) {
      const otherTodoProps = {
        title: todo,
        status: "todo",
        description: "",
      };
      addTodo(otherTodoProps);
    }
  };

  const handleAddTodoClick = () => {
    prepareAndAddTodo(todoToAdd);
    todoToAdd = "";
  };

  const handleAddTodoEnter = (event) => {
    if (event.code === "Enter") {
      if (todoToEdit) {
        handleEditTodoClick();
      } else {
        prepareAndAddTodo(todoToAdd);
        todoToAdd = "";
      }
    }
  };

  const handleEditTodoClick = () => {
    if (todoToAdd) {
      editTodo(todoToAdd);
    }
    todoToAdd = "";
    todoToEdit = "";
  };
</script>

<div class="inline-flex justify-center items-center w-full">
  <input
    class="w-full outline-none rounded-sm bg-blue-50 h-7 p-2"
    bind:value={todoToAdd}
    on:keypress={handleAddTodoEnter}
    maxlength="50"
  />
  <div
    class="h-6 ml-4 hover:text-blue-50 hover:cursor-pointer"
    on:click={() => {
      todoToEdit ? handleEditTodoClick() : handleAddTodoClick();
    }}
  >
    {#if todoToEdit}
      <FaPencilAlt />
    {:else}
      <FaPlus />
    {/if}
  </div>
</div>
