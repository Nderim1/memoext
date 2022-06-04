<script>
  import { onMount } from "svelte";

  import FaArrowRight from "svelte-icons/fa/FaArrowRight.svelte";

  export let notes;
  export let handleOnNoteClick;
</script>

{#each notes as note, index}
  <!-- <EditNote {note} /> -->
  <div
    class="mb-4 p-2 w-full justify-between rounded-sm inline-flex cursor-pointer border-blue-50 border hover:bg-slate-100"
    on:click={() => handleOnNoteClick(index)}
  >
    <div>
      <span class="text-lg font-medium">{note.title}</span><br />
      <p class="descriptionPeak text-sm">{note.text || ""}</p>
    </div>
    <div class="minWidth w-5 self-center flex ml-2">
      <FaArrowRight />
    </div>
  </div>
{/each}

<style>
  .descriptionPeak {
    overflow: hidden;
    text-overflow: ellipsis;

    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
  }

  .minWidth {
    min-width: 20px;
  }
</style>
