<script>
 import Card from "../lib/card.svelte"
    let searchResults = [];
    export var searchTerm = ``
$: {
    if (searchTerm) {
        fetchResults(searchTerm)
    }
}
    async function fetchResults(term) {
        const itunesSearched = await fetch(`https://itunes.apple.com/search?term=${term}&entity=song`);
      var res = await itunesSearched.json();
      searchResults = res.results;
      console.log(searchResults)
    }
    
  </script>
  
  <section>
      
    <input
	class="w-full flex rounded-md bg-white bg-opacity-20 p-1 border border-white border-opacity-30"
	bind:value={searchTerm}
	type="text"
	placeholder="Search songs..."
/>

    <div class="py-4 gap-4 grid md:grid-cols-3 grid-cols-1">
        {#each searchResults as item}
            <p>
                <Card cardItem={item} />
            </p>
        {/each}
    </div>


  </section>