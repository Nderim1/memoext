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
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi vehicula enim
  sit amet magna lacinia, id luctus libero semper. Aenean eget urna et enim
  ultrices porttitor. Nulla id feugiat sem. Fusce commodo, est nec placerat
  consequat, turpis quam faucibus dolor, nec malesuada augue enim a justo. Proin
  malesuada semper condimentum. Nulla tristique egestas tellus, vel posuere
  libero lacinia ac. Morbi vel mauris eu est hendrerit imperdiet sit amet
  placerat elit. Nulla luctus, odio maximus bibendum pulvinar, nibh nulla
  vehicula turpis, at cursus odio felis at odio. Nullam placerat, nunc id semper
  convallis, magna tellus vulputate tellus, a rhoncus leo risus eu elit.
  Curabitur egestas eros efficitur, efficitur est vitae, sollicitudin dui.
  Nullam sapien nisl, placerat sed risus sed, tincidunt dictum velit. Vivamus
  fermentum lobortis nisl at ornare. Donec non nulla sapien. Vestibulum ante
  ipsum primis in faucibus orci luctus et ultrices posuere cubilia curae;
  Phasellus tincidunt, ipsum tincidunt scelerisque cursus, metus orci efficitur
  massa, nec rhoncus libero ante a felis. Vestibulum ante ipsum primis in
  faucibus orci luctus et ultrices posuere cubilia curae; Donec quis ultricies
  arcu. Nunc vulputate nec enim id porta. Nullam vulputate placerat lacus ut
  aliquet. In quis eleifend lectus, quis semper nulla. Vivamus placerat, ex vel
  consequat posuere, mauris purus semper tortor, in pharetra mauris nunc eget
  dui. Vivamus facilisis commodo tortor a congue. Donec sed euismod tellus.
  Phasellus sed odio tellus. Quisque feugiat, magna ut gravida cursus, libero
  nisi sodales urna, quis varius sapien lacus non ipsum. Phasellus vitae mauris
  ac felis aliquet lacinia ut rutrum risus. Curabitur vel hendrerit ante, ut
  gravida tortor. In dapibus dolor ut placerat mollis. Donec et nisl dictum,
  blandit est id, rhoncus ipsum. Maecenas facilisis tellus vel lectus
  pellentesque venenatis. Praesent iaculis sagittis ex at semper. Maecenas porta
  mi quam, luctus finibus ex vulputate et. Maecenas facilisis luctus turpis, vel
  finibus ligula venenatis fringilla. Ut semper lorem a iaculis malesuada. Sed
  et convallis felis, in blandit elit. Nullam ornare nibh sed quam ornare
  suscipit. Integer at quam consectetur, tempus metus et, euismod lorem. Nunc eu
  nunc nibh. Duis ex sapien, lacinia et enim eget, pharetra fringilla sapien.
  Proin at risus facilisis, dapibus magna quis, faucibus neque. Pellentesque eu
  magna luctus, ultrices sapien vitae, blandit velit. Etiam nulla ex, gravida in
  auctor non, dignissim eu libero. Orci varius natoque penatibus et magnis dis
  parturient montes, nascetur ridiculus mus. Donec at rhoncus dui, at cursus mi.
  Fusce vitae imperdiet ex. Sed condimentum mollis varius. Ut eget lorem at diam
  ultricies luctus sed in elit. Nam efficitur nec lacus ac ornare. Aliquam erat
  volutpat. Integer sem mi, imperdiet sit amet auctor ac, vulputate at neque.
  Sed vel nulla nec libero commodo sodales sit amet nec mauris. Maecenas laoreet
  ligula in mi consequat, quis lacinia urna tempus. Orci varius natoque
  penatibus et magnis dis parturient montes, nascetur ridiculus mus. Maecenas
  pretium in elit quis dignissim. Etiam mattis imperdiet enim. Aenean venenatis
  felis a risus interdum interdum. Aenean consectetur dapibus libero ut mollis.
  Nulla in ligula et nibh congue blandit. Mauris maximus vitae purus vel auctor.
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi vehicula enim
  sit amet magna lacinia, id luctus libero semper. Aenean eget urna et enim
  ultrices porttitor. Nulla id feugiat sem. Fusce commodo, est nec placerat
  consequat, turpis quam faucibus dolor, nec malesuada augue enim a justo. Proin
  malesuada semper condimentum. Nulla tristique egestas tellus, vel posuere
  libero lacinia ac. Morbi vel mauris eu est hendrerit imperdiet sit amet
  placerat elit. Nulla luctus, odio maximus bibendum pulvinar, nibh nulla
  vehicula turpis, at cursus odio felis at odio. Nullam placerat, nunc id semper
  convallis, magna tellus vulputate tellus, a rhoncus leo risus eu elit.
  Curabitur egestas eros efficitur, efficitur est vitae, sollicitudin dui.
  Nullam sapien nisl, placerat sed risus sed, tincidunt dictum velit. Vivamus
  fermentum lobortis nisl at ornare. Donec non nulla sapien. Vestibulum ante
  ipsum primis in faucibus orci luctus et ultrices posuere cubilia curae;
  Phasellus tincidunt, ipsum tincidunt scelerisque cursus, metus orci efficitur
  massa, nec rhoncus libero ante a felis. Vestibulum ante ipsum primis in
  faucibus orci luctus et ultrices posuere cubilia curae; Donec quis ultricies
  arcu. Nunc vulputate nec enim id porta. Nullam vulputate placerat lacus ut
  aliquet. In quis eleifend lectus, quis semper nulla. Vivamus placerat, ex vel
  consequat posuere, mauris purus semper tortor, in pharetra mauris nunc eget
  dui. Vivamus facilisis commodo tortor a congue. Donec sed euismod tellus.
  Phasellus sed odio tellus. Quisque feugiat, magna ut gravida cursus, libero
  nisi sodales urna, quis varius sapien lacus non ipsum. Phasellus vitae mauris
  ac felis aliquet lacinia ut rutrum risus. Curabitur vel hendrerit ante, ut
  gravida tortor. In dapibus dolor ut placerat mollis. Donec et nisl dictum,
  blandit est id, rhoncus ipsum. Maecenas facilisis tellus vel lectus
  pellentesque venenatis. Praesent iaculis sagittis ex at semper. Maecenas porta
  mi quam, luctus finibus ex vulputate et. Maecenas facilisis luctus turpis, vel
  finibus ligula venenatis fringilla. Ut semper lorem a iaculis malesuada. Sed
  et convallis felis, in blandit elit. Nullam ornare nibh sed quam ornare
  suscipit. Integer at quam consectetur, tempus metus et, euismod lorem. Nunc eu
  nunc nibh. Duis ex sapien, lacinia et enim eget, pharetra fringilla sapien.
  Proin at risus facilisis, dapibus magna quis, faucibus neque. Pellentesque eu
  magna luctus, ultrices sapien vitae, blandit velit. Etiam nulla ex, gravida in
  auctor non, dignissim eu libero. Orci varius natoque penatibus et magnis dis
  parturient montes, nascetur ridiculus mus. Donec at rhoncus dui, at cursus mi.
  Fusce vitae imperdiet ex. Sed condimentum mollis varius. Ut eget lorem at diam
  ultricies luctus sed in elit. Nam efficitur nec lacus ac ornare. Aliquam erat
  volutpat. Integer sem mi, imperdiet sit amet auctor ac, vulputate at neque.
  Sed vel nulla nec libero commodo sodales sit amet nec mauris. Maecenas laoreet
  ligula in mi consequat, quis lacinia urna tempus. Orci varius natoque
  penatibus et magnis dis parturient montes, nascetur ridiculus mus. Maecenas
  pretium in elit quis dignissim. Etiam mattis imperdiet enim. Aenean venenatis
  felis a risus interdum interdum. Aenean consectetur dapibus libero ut mollis.
  Nulla in ligula et nibh congue blandit. Mauris maximus vitae purus vel auctor.
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
