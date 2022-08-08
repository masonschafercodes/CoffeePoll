<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	import Trash from 'phosphor-svelte/lib/Trash';

	interface IOptions {
		id: number;
		value: string;
	}

	let isMulti: boolean = false;
	let question: string = '';
	let options: IOptions[] = [{ id: 1, value: '' }];
	let userId = crypto.randomUUID();

	function handleAddOption() {
		options = [...options, { id: options.length + 1, value: '' }];
	}

	function handleRemoveOption(id: number) {
		options = options.filter((option) => option.id !== id);
	}

	const dispatch = createEventDispatcher();

	const onSubmit = (): void => {
		dispatch('submit', { isMulti, question, options, userId });
	};
</script>

<form class="mt-6 space-y-4" on:submit|preventDefault={onSubmit}>
	<div class="flex flex-col gap-2">
		<label for="pollTitle" class="font-brand text-gray-600 font-semibold">Poll Title</label>
		<input
			type="text"
			id="pollTitle"
			bind:value={question}
			class="px-2 py-1.5 font-brand rounded border-2 border-gray-100 focus:border-yellow-500"
		/>
	</div>
	<div class="relative flex items-center py-4 font-brand">
		<div class="min-w-0 flex-1 text-sm">
			<label for="multi" class="font-semibold text-gray-600">Multi-Select</label>
			<p id="multi-description" class="text-gray-500">Enable Multi-Select for this poll</p>
		</div>
		<div class="ml-3 flex items-center h-5">
			<input
				id="multi"
				aria-describedby="multi-description"
				bind:checked={isMulti}
				name="multi"
				type="checkbox"
				class="focus:ring-yellow-500 h-4 w-4 text-yellow-600 border-gray-300 rounded"
			/>
		</div>
	</div>
	<div class="flex flex-col gap-2">
		{#each options as option (option.id)}
			<label for="option" class="font-brand text-gray-600 font-semibold"
				>Poll Option {option.id}</label
			>
			<div class="w-full flex gap-2">
				<input
					type="text"
					id="option"
					bind:value={option.value}
					class="px-2 py-1.5 rounded font-brand  border-2 border-gray-100 focus:border-yellow-500 w-full"
				/>
				<button on:click={() => handleRemoveOption(option.id)}>
					<Trash size={24} color="#ff6363" />
				</button>
			</div>
		{/each}
	</div>
	<div>
		<button
			type="button"
			on:click={handleAddOption}
			class="text-yellow-700 border-2 border-yellow-200 border-dashed hover:border-yellow-300 transition ease-in-out delay-100 px-4 py-1.5 font-brand font-semibold rounded w-full"
		>
			Add Another Option
		</button>
	</div>
	<div class="mt-12">
		<button
			type="submit"
			class="bg-yellow-100 text-yellow-700 hover:bg-yellow-200 transition ease-in-out delay-100 px-4 py-1.5 font-brand font-semibold rounded w-full"
		>
			Create a Poll
		</button>
	</div>
</form>
