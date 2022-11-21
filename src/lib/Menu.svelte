<script>
	export let def; // array of menu items

  const menuDiv = "---";  

  let isOpened = false;

  function fixMenuName(s) {
    return s.replace("&", "");
  }

  function toggleOpened() {
    isOpened = !isOpened;
  }

  function eatClick(ev) {
    console.log("eat:", ev);  
    ev.preventDefault();
    ev.stopPropagation();
  }

  function menuClicked(mi) {
    
    console.log(mi);
  }
</script>

<div class="mr-2 hover:bg-gray-300 cursor-pointer" on:click={toggleOpened}>{fixMenuName(def[0])}  
  {#if isOpened}
    <div class="menu absolute flex flex-col bg-white px-2 py-2 border-2 z-40 text-sm">
          {#each def[1] as mi}
        {#if mi === menuDiv}
          <hr class="mt-2 mb-2" on:click={eatClick}>
        {:else}
            <div class="flex flex-row justify-between	 hover:bg-gray-100" on:click="{menuClicked(mi)}">
                <div>{mi[0]}</div>
                <div class="ml-4 text-gray-500">{mi[2] || " "}</div>
            </div>
        {/if}
          {/each}
    </div>
  {/if}
</div>

<style>
  .menu {
    grid-template-columns: auto auto auto;
  }
</style>
