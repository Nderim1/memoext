<script>
  import ShowNotes from "./ShowNotes/index.svelte";
  import EditNote from "./EditNote/index.svelte";
  import FaArrowLeft from "svelte-icons/fa/FaArrowLeft.svelte";
  import { onMount } from "svelte";
  import FaCheckCircle from "svelte-icons/fa/FaCheckCircle.svelte";
  import FaTrashAlt from "svelte-icons/fa/FaTrashAlt.svelte";

  let componentToShow = "notes";
  let createMode = false;
  let noteToEdit = {};
  let noteToEditIndex = -1;
  let showBackArrow = false;
  let allNotes = [];
  let newNoteInfo = {};
  let isNoteSaved = true;

  const updateLSNotes = (notes) => {
    localStorage.setItem("memo.notes", JSON.stringify(notes));
  };

  const navigateTo = (here) => {
    componentToShow = here;
  };

  const handleOnNoteClick = (noteIndex) => {
    noteToEdit = allNotes[noteIndex];
    noteToEditIndex = noteIndex;
    newNoteInfo = {};
    navigateTo("edit");
  };

  const handleCreateNoteClick = () => {
    noteToEdit = {};
    createMode = true;
    navigateTo("edit");
  };

  const handleOnSaveNoteClick = () => {
    if (createMode) {
      if (!newNoteInfo.title) {
        return;
      }
      allNotes.unshift(newNoteInfo);
    } else {
      allNotes[noteToEditIndex] = newNoteInfo;
    }

    isNoteSaved = true;
    updateLSNotes(allNotes);
    navigateTo("notes");
  };

  const handleNoteDelete = () => {
    if (noteToEditIndex !== -1) {
      allNotes.splice(noteToEditIndex, 1);
      updateLSNotes(allNotes);
      navigateTo("notes");
    }
  };

  const handleOnNoteChange = ({ title, text, plainText }) => {
    newNoteInfo = { title, text, plainText };
    isNoteSaved = false;
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
    console.log(LSNotes);
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
        title="Back"
        on:click={() => {
          let isConfirmed = false;
          if (!isNoteSaved) {
            isConfirmed = confirm(
              "Your note is not saved. Are you sure you want to go back?"
            );

            if (isConfirmed) {
              newNoteInfo = {};
              isNoteSaved = true;
              navigateTo("notes");
            }
          } else {
            newNoteInfo = {};
            isNoteSaved = true;
            navigateTo("notes");
          }
        }}
      >
        <FaArrowLeft />
      </div>
      <div class="inline-flex items-center">
        <div
          on:click={() => handleNoteDelete()}
          class="w-4 mr-3 cursor-pointer hover:text-blue-50"
          title="Delete"
        >
          <FaTrashAlt />
        </div>
        {#if isNoteSaved}
          <div class="w-4 mr-2" title="Saved!">
            <FaCheckCircle />
          </div>
        {/if}
        <button
          class="float-right w-16 rounded-sm border border-blue-50 hover:bg-blue-50"
          title="Save"
          on:click={() => handleOnSaveNoteClick()}>Save</button
        >
      </div>
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
