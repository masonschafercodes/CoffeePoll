<script lang="ts">
	import '../app.css';
	import NavbarTopLink from '../components/NavbarTopLink.svelte';

	interface NavbarTopLink {
		linkName: string;
		linkUrl: string;
	}

	const links: NavbarTopLink[] = [
		{ linkName: 'About', linkUrl: '/about' },
		{ linkName: 'Create a Poll', linkUrl: '/poll' }
	];
</script>

<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous" />
	<link
		href="https://fonts.googleapis.com/css2?family=Work+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;1,300;1,400;1,500;1,600;1,700;1,800&display=swap"
		rel="stylesheet"
	/>
</svelte:head>

<div>
	<div class="border-b border-gray-100">
		<div class="max-w-4xl lg:mx-auto mx-2">
			<div class="flex items-center justify-between w-full py-4">
				<div class="flex items-center gap-2">
					<a href="/" class="flex items-center gap-2 text-xl font-bold text-gray-700 font-brand"
						>CoffeePoll<span
							class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-yellow-100 text-yellow-800"
						>
							BETA
						</span></a
					>
					<div>
						<div class="space-x-2 font-medium text-sm text-gray-600">
							{#each links as link}
								<NavbarTopLink linkName={link.linkName} linkUrl={link.linkUrl} />
							{/each}
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
	<div class="mt-12 max-w-4xl mx-2 lg:mx-auto selection:bg-yellow-100">
		<slot />
	</div>
</div>
