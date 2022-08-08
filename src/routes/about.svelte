<script>
	import GithubLogo from 'phosphor-svelte/lib/GithubLogo';
	import Package from 'phosphor-svelte/lib/Package';
</script>

<svelte:head>
	<title>CoffeePoll | About</title>
</svelte:head>

<div class="flex flex-col items-center justify-center">
	<h1 class="text-2xl font-semibold font-brand text-gray-700">Easy Polling</h1>
	<p class="text-center text-sm font-brand text-gray-600 mt-2">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Vel aspernatur ullam sequi saepe
		facilis cum nam in soluta repellendus, enim corporis, cupiditate numquam! Hic, omnis. Et
		blanditiis quas illum quibusdam?
	</p>
	<div class="mt-12 flex gap-4 items-center justify-center">
		<div class="p-1.5 bg-gray-100 rounded-full">
			<GithubLogo size={24} color="#6f7270" />
		</div>
		<div class="p-1.5 bg-gray-100 rounded-full">
			<Package size={24} color="#6f7270" />
		</div>
	</div>
</div>
