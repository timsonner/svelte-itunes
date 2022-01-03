  <script>
    import { fade } from 'svelte/transition';
    export let cardItem
</script>

<a class="no-underline p-6 bg-gray-800 text-gray-500 text-center rounded-md shadow-lg hover:bg-green-700 border-2 border-gray-200 flex flex-col items-center"
href={`/${cardItem.trackId}`} transition:fade>
<!-- padding 6, background gray, text gray, center text, rounded border, box shadow, flex, column flex, center items -->
    <img class="h-40 w-40" src={cardItem.artworkUrl100} alt="Album art">
<div class="mb-2 h-6 overflow-hidden pb-8">{cardItem.trackName}</div>
        <div class="text-xs font-bold">{cardItem.artistName}</div>
</a>