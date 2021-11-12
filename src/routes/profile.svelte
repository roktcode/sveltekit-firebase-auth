<script>
	import { user, isLoggedIn } from "../stores";
</script>

<h1>Profile page</h1>

{#if isLoggedIn}
	<div class="profile">
		<img width="80" height="80" src={$user.photoURL} alt="avatar" />
		<h4>{$user.displayName}</h4>
		<p>Your email is: {$user.email}</p>
	</div>
{/if}

<style>
	.profile {
		max-width: 500px;
		display: grid;
		place-items: center;
		border: 1px solid #ddd;
		margin: 20px;
		padding: 20px;
	}

	h4 {
		margin: 0;
	}

	img {
		border-radius: 50%;
		margin-bottom: 10px;
	}
</style>
