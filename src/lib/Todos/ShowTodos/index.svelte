<script>
  import { onMount } from "svelte";
  export let allTodos;
  export let handleOnCheckboxCheck;
  export let removeTodo;
  export let editTodo;
  import BuildTodo from "./BuildTodo/index.svelte";
</script>

<div class="justify-center overflow-y-scroll min-h-48 pt-3">
  {#if allTodos.length}
    {#each allTodos as todo, index}
      {#if todo.title.length}
        <BuildTodo
          key={index}
          todoToDisplay={todo}
          onCheckboxCheck={(status) => handleOnCheckboxCheck(index, status)}
          handleOnEditTodo={() => editTodo(index)}
          removeTodo={() => removeTodo(index)}
        />
      {/if}
    {/each}
  {:else}
    <span class="text-sm">You have no TODOs at the moment!</span>
  {/if}
</div>
