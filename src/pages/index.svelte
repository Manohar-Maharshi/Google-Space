<script>
	import { url } from '@roxi/routify';
	import { goto } from '@roxi/routify';
	import { results } from '@/components/MockResult';


	let term = "";


	const getTermFromInput = () =>{
		if(term){
 			fetchDataFromTerm(term);
			$goto('../search/',{term})
		}else{

		}

	}

	const fetchDataFromTerm = async (term) =>{
		$results = {};
	  	const url = `https://www.googleapis.com/customsearch/v1?key=AIzaSyATTNBp3EknQRSvCJJiHVx-uO1hfAb-FHo&cx=74efad55360d3bbbb&q=${term}`
	 	const res = await fetch(url);
	 	const json = await res.json()
	 	$results = json;
	 	$results = $results;
  	}
</script>

<main class="flex flex-col items-center justify-center">
	<img class="w-auto" src="https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png" alt="Google logo">
	<form on:submit|preventDefault={getTermFromInput} class="flex flex-col items-center mt-5 ">
		<div class="inline-flex items-center space-between border rounded-full px-1 group">
			<svg focusable="false" class="h-4.5 w-4.5 fill-gray-500 ml-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M15.5 14h-.79l-.28-.27A6.471 6.471 0 0 0 16 9.5 6.5 6.5 0 1 0 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"></path></svg>
			<input bind:value={term} class="group-hover:shadow flex-1 border-0 outline-none px-2 py-2.5 text-md w-lg" type="text" name="Search google">
			<svg class="h-6 w-6 mr-3 cursor-pointer" focusable="false" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path fill="#4285f4" d="m12 15c1.66 0 3-1.31 3-2.97v-7.02c0-1.66-1.34-3.01-3-3.01s-3 1.34-3 3.01v7.02c0 1.66 1.34 2.97 3 2.97z"></path><path fill="#34a853" d="m11 18.08h2v3.92h-2z"></path><path fill="#fbbc05" d="m7.05 16.87c-1.27-1.33-2.05-2.83-2.05-4.87h2c0 1.45 0.56 2.42 1.47 3.38v0.32l-1.15 1.18z"></path><path fill="#ea4335" d="m12 16.93a4.97 5.25 0 0 1 -3.54 -1.55l-1.41 1.49c1.26 1.34 3.02 2.13 4.95 2.13 3.87 0 6.99-2.92 6.99-7h-1.99c0 2.92-2.24 4.93-5 4.93z"></path></svg>
		</div>
		<a href="./search?term=:term" use:$url={{term:term}} class="{ term ? 'text-gray-700' : 'pointer-events-none' } select-none border px-5 p-2 mt-7 mb-10 text-sm rounded text-gray-700 bg-gray-200 hover:(shadow)" type="submit">Google Search</a>
	</form>
</main>