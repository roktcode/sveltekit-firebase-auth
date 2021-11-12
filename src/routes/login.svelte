<script>
	import { initializeApp } from "firebase/app";
	import { GoogleAuthProvider, signInWithPopup, getAuth } from "firebase/auth";
	import { firebaseConfig } from "../firebase";
	import { isLoggedIn, user } from "../stores.js";
	import { goto } from "$app/navigation";
	// Initialize Firebase
	const app = initializeApp(firebaseConfig);

	const auth = getAuth();
	const googlePrvider = new GoogleAuthProvider();

	async function login() {
		try {
			const result = await signInWithPopup(auth, googlePrvider);
			const credential = GoogleAuthProvider.credentialFromResult(result);
			const token = credential.accessToken;
			// The signed-in user info.
			$user = result.user;
			$isLoggedIn = true;
			goto("/profile");
		} catch (error) {
			console.error(error);
		}
	}
</script>

<h1>Login page</h1>
<button on:click={login}>Login with Google</button>
