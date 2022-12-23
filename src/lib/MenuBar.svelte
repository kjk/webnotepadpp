<script lang="ts">
  import Menu from "./Menu.svelte";

  export let def; // definition of the menubar

  function fixMenuName(s) {
    return s.replace("&", "");
  }
</script>

<div class="flex flex-row bg-gray-50 px-2 relative">
  {#each def as menu}
    <Menu def={menu}></Menu>
  {/each}
</div>

<style>
</style>
