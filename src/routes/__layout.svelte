<script>
	import { isLoggedIn, user } from "../stores";
	import { signOut, getAuth } from "firebase/auth";

	async function logout() {
		try {
			await signOut(getAuth());
			$user = {};
			$isLoggedIn = false;
		} catch (error) {
			console.error(error);
		}
	}
</script>

<nav>
	<ul>
		<li><a href="/">Home</a></li>
		<li><a href="/profile">Profile</a></li>
		{#if $isLoggedIn}
			<li><a on:click={logout}>Logout</a></li>
		{:else}
			<li><a href="/login">Login</a></li>
		{/if}
	</ul>
</nav>

<slot />

<style>
	ul {
		list-style-type: none;
		display: flex;
		margin: 0;
		padding: 0;
		gap: 1rem;
	}

	li {
		font-weight: bold;
	}

	a {
		text-decoration: none;
		color: #333;
	}

	a:hover {
		text-decoration: underline;
	}
</style>
