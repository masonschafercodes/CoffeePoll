<script lang="ts">
	import { createEventDispatcher } from 'svelte';

	let email: string;
	let password: string;

	const dispatch = createEventDispatcher();

	const onSubmit = (): void => {
		dispatch('submit', { email, password });
	};
</script>

<form class="mt-4 font-brand" on:submit|preventDefault={onSubmit}>
	<div class="flex flex-col gap-2">
		<label for="email" class="font-brand text-gray-600">Email</label>
		<input
			type="email"
			id="email"
			bind:value={email}
			class="px-2 py-1.5 rounded border-2 border-gray-100 focus:border-yellow-500"
		/>
	</div>
	<div class="flex flex-col gap-2 mt-2">
		<label for="password" class="font-brand text-gray-600">Password</label>
		<input
			type="password"
			id="password"
			bind:value={password}
			class="px-2 py-1.5 rounded border-2 border-gray-100"
		/>
	</div>
	<div class="mt-4">
		<button
			type="submit"
			class="bg-yellow-100 text-yellow-700 hover:bg-yellow-200 transition ease-in-out delay-100 px-4 py-1.5 font-brand font-semibold rounded w-full"
		>
			Login
		</button>
	</div>
</form>
