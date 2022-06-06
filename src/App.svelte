<script>
  import "./app.css";
  import FaPencilRuler from "svelte-icons/fa/FaPencilRuler.svelte";
  import Home from "./lib/Home.svelte";

  let showHome = false;
  const setShowHome = (isShowHome) => {
    showHome = isShowHome;
  };
</script>

<main>
  {#if showHome}
    <Home {setShowHome} />
  {/if}
  <button
    type="button"
    data-mdb-ripple="true"
    data-mdb-ripple-color="light"
    class="inline-block p-3 bg-slate-800 text-white hover:text-slate-800 font-medium text-xs leading-tight uppercase rounded-full shadow-md hover:bg-blue-50 hover:shadow-lg focus:shadow-lg focus:outline-none focus:ring-0 active:shadow-lg transition duration-150 ease-in-out bottom-5 right-5 fixed"
    id="btn-back-to-top"
    on:click={() => setShowHome(!showHome)}
  >
    <div class="w-5"><FaPencilRuler /></div>
  </button>
</main>

<style>
  main {
    background-color: rgb(235, 235, 238);
  }
</style>
