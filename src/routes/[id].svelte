<script context="module">
  
	export async function load({ params, fetch }) {
		const url = `https://itunes.apple.com/search?term=${params.id}&entity=song`;
		const urlResponse = await fetch(url); // get the response returns a promise, so we await
		const responseData = await urlResponse.json(); // get data from the response, return it as json
		const result = responseData.results[0] // give first object in response
    console.log(result)
		return { props: {result} }
	}
</script>

<script>
    export let result
</script>
<section>
    <div class="mt-12 flex flex-col items-center justify-center">
        <h1 class="text-3xl font-bold text-center mb-4">{result.trackName}</h1>
        <img src={result.artworkUrl100} alt="img" class="w-1/4 rounded-md">
        <h1 class="text-2xl font-bold text-center mb-6">{result.artistName}</h1>
        <audio controls>
          <source src={result.previewUrl} type="audio/mpeg">
        </audio>
      </div>
</section>