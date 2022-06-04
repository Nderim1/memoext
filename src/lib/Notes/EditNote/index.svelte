<script>
  import { onMount } from "svelte";
  // import Editor, { tinymce } from "@tinymce/tinymce-svelte";

  export let note;
  export let handleOnNoteChange;
  let editor;

  export let toolbarOptions = [
    [
      { header: 1 },
      { header: 2 },
      "blockquote",
      "link",
      "bold",
      "italic",
      "underline",
      "strike",
      { list: "ordered" },
      { list: "bullet" },
    ],
  ];

  let titleValue = note.title || "";
  let textValue = note.text || "";

  let noteTitleInput;

  onMount(async () => {
    const { default: Quill } = await import("quill");
    noteTitleInput.focus();

    let quill = new Quill(editor, {
      modules: {
        toolbar: toolbarOptions,
      },
      theme: "snow",
      placeholder: "Quick note here...",
    });

    quill.root.innerHTML = textValue && JSON.parse(textValue);

    quill.on("text-change", function (delta, oldDelta, source) {
      let contents = quill.getContents();
      console.log("contents", contents);
      if (
        source == "user" &&
        textValue !== JSON.stringify(quill.root.innerHTML)
      ) {
        handleOnNoteChange({
          title: titleValue,
          text: JSON.stringify(quill.root.innerHTML),
          plainText: quill.getContents().ops[0].insert,
        });
      }
    });
  });
</script>

<div class="h-5/6">
  <input
    bind:this={noteTitleInput}
    bind:value={titleValue}
    on:input={() => handleOnNoteChange({ title: titleValue, text: textValue })}
    class="w-full mb-3 outline-none rounded-sm bg-blue-50 h-7 p-2"
  />
  <!-- <Editor /> -->
  <!-- <textarea
    bind:value={textValue}
    on:input={() => handleOnNoteChange({ title: titleValue, text: textValue })}
    class="w-full h-4/6 outline-none rounded-sm bg-blue-50 h-7 p-2"
  /> -->

  <div class="editor-wrapper border-2 border-blue-50">
    <div bind:this={editor} />
  </div>
</div>

<style>
  @import "https://cdn.quilljs.com/1.3.6/quill.snow.css";
</style>
