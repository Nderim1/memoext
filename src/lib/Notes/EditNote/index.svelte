<script>
  export let note;
  export let handleOnNoteChange;

  let titleValue = note.title || "";
  let textValue = note.text || "";

  $: {
    console.log(titleValue, note.title);
    handleOnNoteChange({ title: titleValue, text: textValue });
  }
</script>

<div class="h-5/6">
  <input
    bind:value={titleValue}
    class="w-full mb-3 outline-none rounded-sm bg-blue-50 h-7 p-2"
  />
  <textarea
    bind:value={textValue}
    class="w-full h-4/6 outline-none rounded-sm bg-blue-50 h-7 p-2"
  />
</div>
