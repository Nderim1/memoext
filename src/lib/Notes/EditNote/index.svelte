<script>
  import { onMount } from "svelte";

  export let note;
  export let handleOnNoteChange;

  let titleValue = note.title || "";
  let textValue = note.text || "";

  let noteTitleInput;

  onMount(() => noteTitleInput.focus());
</script>

<div class="h-5/6">
  <input
    bind:this={noteTitleInput}
    bind:value={titleValue}
    on:input={() => handleOnNoteChange({ title: titleValue, text: textValue })}
    class="w-full mb-3 outline-none rounded-sm bg-blue-50 h-7 p-2"
  />
  <textarea
    bind:value={textValue}
    on:input={() => handleOnNoteChange({ title: titleValue, text: textValue })}
    class="w-full h-4/6 outline-none rounded-sm bg-blue-50 h-7 p-2"
  />
</div>
