<script>
	import { params } from '@roxi/routify';
	import { goto } from '@roxi/routify';
	import { results } from '@/components/MockResult';



	let term = $params.term;


	const getTermFromInput = () =>{
		if(term){
 			fetchDataFromTerm(term)
			$goto('../search/',{term})
		}
	}
	const fetchDataFromTerm = async (term) =>{
		$results = {};
	  	const url = `https://www.googleapis.com/customsearch/v1?key=AIzaSyATTNBp3EknQRSvCJJiHVx-uO1hfAb-FHo&cx=74efad55360d3bbbb&q=${term}&start=1`
	 	const res = await fetch(url);
	 	const json = await res.json()
	 	$results = json;
	 	$results = $results;
  	}
</script>

<main class="py-5 flex items-center justify-between">
	<a href="/" class="w-24">
		<img class="w-full" src="https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" alt="google">
	</a>
	<form on:submit|preventDefault={getTermFromInput} class="shadow-md inline-flex items-center space-between border rounded-full px-1 ">
		<svg focusable="false" class="h-4.5 w-4.5 fill-gray-500 ml-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M15.5 14h-.79l-.28-.27A6.471 6.471 0 0 0 16 9.5 6.5 6.5 0 1 0 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"></path></svg>
		<input bind:value={term} class="flex-1 border-0 outline-none px-2 py-2.5 text-md w-lg" type="text" name="Search google">
		<svg class="h-6 w-6 mr-3 cursor-pointer" focusable="false" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path fill="#4285f4" d="m12 15c1.66 0 3-1.31 3-2.97v-7.02c0-1.66-1.34-3.01-3-3.01s-3 1.34-3 3.01v7.02c0 1.66 1.34 2.97 3 2.97z"></path><path fill="#34a853" d="m11 18.08h2v3.92h-2z"></path><path fill="#fbbc05" d="m7.05 16.87c-1.27-1.33-2.05-2.83-2.05-4.87h2c0 1.45 0.56 2.42 1.47 3.38v0.32l-1.15 1.18z"></path><path fill="#ea4335" d="m12 16.93a4.97 5.25 0 0 1 -3.54 -1.55l-1.41 1.49c1.26 1.34 3.02 2.13 4.95 2.13 3.87 0 6.99-2.92 6.99-7h-1.99c0 2.92-2.24 4.93-5 4.93z"></path></svg>
	</form>
	<div class="flex items-center space-x-3">
		<a href="https://github.com/Manohar-Maharshi/Google-Space" target="_blank" class="h-8 w-8 bg-blue-200 rounded-full hover:shadow">
			<svg role="img" class="fill-dark-900 stroke-yellow-500" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg>
		</a>
	</div>
</main>