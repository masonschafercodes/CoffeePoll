<script lang="ts">
	import LoginForm from '../components/LoginForm.svelte';

	interface IUser {
		email: string;
		password: string;
	}

	function handleLoginSubmit(event: CustomEvent<IUser>) {
		if (event.detail.password.length < 8) {
			alert('Password must be at least 8 characters long');
			return;
		}

		localStorage.setItem('user', JSON.stringify(event.detail));
	}
</script>

<svelte:head>
	<title>CoffeePoll | Login</title>
</svelte:head>

<div class="flex flex-col items-center justify-center w-full">
	<div>
		<h1 class="font-brand text-2xl text-gray-600 font-semibold">Login to CoffeePoll</h1>
	</div>
	<div class="w-1/2">
		<LoginForm on:submit={handleLoginSubmit} />
	</div>
</div>
