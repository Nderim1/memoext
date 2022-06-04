<script>
  import ShowNotes from "./ShowNotes/index.svelte";
  import EditNote from "./EditNote/index.svelte";
  import CreateNote from "./CreateNote/index.svelte";
  import FaArrowLeft from "svelte-icons/fa/FaArrowLeft.svelte";
  import { onMount } from "svelte";

  let componentToShow = "notes";
  let createMode = false;
  let noteToEdit = {};
  let noteToEditIndex = "";
  let showBackArrow = false;
  let allNotes = [];

  const updateLSNotes = (notes) => {
    localStorage.setItem("memo.notes", JSON.stringify(notes));
  };

  const handleOnNoteClick = (noteIndex) => {
    componentToShow = "edit";
    noteToEdit = allNotes[noteIndex];
    noteToEditIndex = noteIndex;
  };

  const handleCreateNoteClick = () => {
    noteToEdit = {};
    componentToShow = "edit";
    createMode = true;
  };

  const handleOnSaveNoteClick = () => {
    if (createMode) {
      allNotes.unshift(noteToEdit);
    } else {
    }
  };

  const handleOnNoteChange = ({ title, text }) => {
    console.log(title, text);
    console.log(noteToEdit);
    noteToEdit.title = title;
    noteToEdit.text = text;
  };

  const showComponent = (component) => {
    if (component === "edit") {
      showBackArrow = true;
      return EditNote;
    }

    if (component === "notes") {
      createMode = false;
      showBackArrow = false;
      return ShowNotes;
    }
  };

  onMount(() => {
    const LSNotes = localStorage.getItem("memo.notes");
    if (!LSNotes) {
      updateLSNotes(allNotes);
    } else {
      allNotes = JSON.parse(LSNotes);
    }
  });
</script>

<div class="h-full ">
  {#if showBackArrow}
    <div class="inline-flex w-full justify-between items-start">
      <div
        class="w-5 mb-3 cursor-pointer hover:text-blue-50"
        on:click={() => (componentToShow = "notes")}
      >
        <FaArrowLeft />
      </div>
      <button
        class="float-right w-16 rounded-sm border border-blue-50 hover:bg-blue-50"
        on:click={() => handleOnSaveNoteClick()}>Save</button
      >
    </div>
  {:else}
    <button
      class="w-full h-10 mb-5 rounded-sm hover:bg-blue-50 border border-blue-50"
      on:click={() => handleCreateNoteClick()}>Create a new note!</button
    >
  {/if}
  {#if allNotes.length}
    <svelte:component
      this={showComponent(componentToShow)}
      notes={allNotes}
      {handleOnNoteClick}
      note={noteToEdit}
      {handleOnNoteChange}
    />
  {:else}
    <span class="text-sm">You have no notes at the moment!</span>
  {/if}
</div>
