<script lang="ts">
	import { enhance } from '$root/lib/form';

	async function handleSubmit(event: SubmitEvent) {
		const form = event.target as HTMLFormElement;

		await fetch('/home', {
			method: 'post',
			headers: { accept: 'application/json' },
			body: new FormData(form)
		});

		form.reset();
	}
</script>

<form on:submit|preventDefault={handleSubmit} action="/home" method="post" use:enhance>
	<input
		aria-label="Enter your Tweet"
		name="tweet"
		placeholder="What's your hot take?"
		type="text"
	/>
	<button type="submit">Tweet</button>
</form>

<style>
	.compose {
		display: grid;
		grid-template-columns: min-content 1fr;
		align-items: center;
		gap: var(--spacing-16);
		padding: var(--spacing-16) var(--spacing-24);
		border-bottom: 1px solid var(--color-border-primary);
	}

	img {
		width: 48px;
		height: 48px;
		border-radius: 50%;
	}

	form {
		display: flex;
		align-items: center;
		gap: var(--spacing-16);
	}

	input {
		color: var(--color-text-primary);
		background-color: transparent;
	}

	button {
		min-width: 80px;
		font-size: var(--font-16);
		padding: var(--spacing-16);
	}

	.error {
		color: tomato;
	}
</style>
