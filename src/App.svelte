<script lang="ts">
  import logo from './assets/svelte.png'
  import CodeMirror from "./lib/CodeMirror.svelte";

  let s = "hello\n";
  let v = s;
  for (let i = 0; i < 33; i++) {
    v = v + s;
  }

  // state of current document
  let normalLength = 40;
  let lineCount = 4;
  let posLine = 4;
  let posCol = 1;
  let pos = 41;
  let lineEncoding = "Windows (CRLF)";
  let charEncoding ="UTF-8";
  let typingMode = "INS"; // OVR

  function newFile() {
    console.log("newFile");
  }
</script>

<main class="fixed inset-0 grid">
  <div class="flex text-xs">
    <a class="px-2 hover:bg-gray-200" href="/s/home">home</a>
    <a class="px-2 hover:bg-gray-200" href="/s/prefs">prefs</a>
    <a class="px-2 border-t-2 hover:bg-gray-200" href="/f/foo.txt">foo.txt</a>
    <button class="px-2 hover:bg-gray-200" onclick={newFile}>+</button>
  </div>
  <div class="min-h-0 overflow-y-hidden">
    <CodeMirror value={v} class="editor"/>
  </div>
  <div class="flex justify-between px-2 bg-gray-50">
    <div>Normal length: {normalLength}</div>
    <div>Lines: {lineCount}</div>
    <div>Ln: {posLine} Col: {posCol} Pos: {pos}</div>
    <div>{lineEncoding}</div>
    <div>{charEncoding}</div>
    <div>{typingMode}</div>
  </div>
</main>

<style>
  main {
    grid-template-rows: auto 1fr auto;
  }

  :global(editor) {
    overflow: hidden;
  }

</style>
