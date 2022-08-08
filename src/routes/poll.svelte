<script lang="ts">
	import NewPollForm from '../components/NewPollForm.svelte';

	interface IOptions {
		id: number;
		value: string;
	}

	interface IPollInputs {
		isMulti: boolean;
		question: string;
		options: IOptions[];
		userId: string;
	}

	function handlePollSubmit(event: CustomEvent<IPollInputs>) {
		console.log(event.detail);
		localStorage.setItem('pollUserId', JSON.stringify(event.detail.userId));
	}
</script>

<svelte:head>
	<title>CoffeePoll | Create a New Poll</title>
</svelte:head>

<div>
	<h1 class="text-3xl font-brand font-semibold text-gray-700">Create a new poll</h1>
	<NewPollForm on:submit={handlePollSubmit} />
</div>
