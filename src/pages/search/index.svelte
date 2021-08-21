<script>
  import { params } from '@roxi/routify'

  import { results } from '@/components/MockResult';
  import Spinner from '@/components/Spinner.svelte';


  	let isEmpty = false;
  	let pageNo = 1;
  	let noPrevPage = false;
  	let term = $params.term;

	$: if(Object.keys($results).length === 0 && $results.constructor === Object) {
    		isEmpty = true
	} else {
    	isEmpty = false;
	}

	const nextPage = () =>{
		pageNo = pageNo + 1;
		fetchDataFromTerm(pageNo,term)
	}

	$: if(pageNo <= 1){
		noPrevPage = true;
	}else{
		noPrevPage = false;
	}

	const prevPage = () =>{
		pageNo = pageNo - 1;
		fetchDataFromTerm(pageNo,term)
	}


	const fetchDataFromTerm = async (pageNo,term) =>{
		$results = {};
	  	const url = `https://www.googleapis.com/customsearch/v1?key=AIzaSyATTNBp3EknQRSvCJJiHVx-uO1hfAb-FHo&cx=74efad55360d3bbbb&q=${term}&start=${pageNo}`
	 	const res = await fetch(url);
	 	const json = await res.json()
	 	$results = json;
	 	$results = $results;
  }


</script>


<main class="container mx-auto h-auto w-3xl overflow-hidden">
	{#if isEmpty}
		<div class="flex items-center justify-center">
			<Spinner />
		</div>
	{:else}
	    <p class="text-blue-gray-600 text-sm">About {$results?.searchInformation?.formattedTotalResults} results ({$results?.searchInformation?.formattedSearchTime} seconds) - page {pageNo}</p>
	    {#each $results?.items as result}
	      <a href={result.link} target="_blank" class="flex flex-col items-start my-4 group">
	          <p class="text-sm -mb-0.5 text-gray-700">{result?.displayLink}</p>
	          <p class="text-lg text-blue-700 font-semibold group-hover:underline">{result?.title}</p>
	          <p class="text-base">{result?.snippet}</p>
	      </a>
	    {/each}
	{/if}
</main>

{#if isEmpty}
{:else}

	<main class="container mx-auto w-2xl h-auto py-6 flex items-center justify-center">
		<svg on:click={prevPage} xmlns="http://www.w3.org/2000/svg" class="{ noPrevPage ? 'pointer-events-none' : 'cursor-pointer' } hover:text-blue-700 h-10 w-10 cursor-pointer rounded-full shadow bg-blue-gray-300" fill="none" viewBox="0 0 24 24" stroke="currentColor">
		  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
		</svg>
		<span class="mx-10 text-center">{pageNo}</span>
		<svg on:click={nextPage} xmlns="http://www.w3.org/2000/svg" class="hover:text-blue-700 h-10 w-10 cursor-pointer rounded-full shadow bg-blue-gray-300" fill="none" viewBox="0 0 24 24" stroke="currentColor">
		  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
		</svg>
	</main>
{/if}



