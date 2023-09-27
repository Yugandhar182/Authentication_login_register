<script>
  import Button from "$lib/Navbar/navbar.svelte";
  import { auth } from '$lib/firebase/firebase.js';
  import { onMount } from 'svelte';
  import { goto } from '$app/navigation';

  let isAuthenticated = false; // Initialize a loading state
  let user = null; // Initialize the user variable

  // Check if the user is authenticated when the component mounts
  onMount(async () => {
    // Check if the user is authenticated
    if (auth.currentUser) {
      isAuthenticated = true; // User is authenticated
      user = auth.currentUser.email;
    } else {
      // If the user is not authenticated, redirect them to the login page
      goto('/'); 
    }
  });
</script>
{#if isAuthenticated}
<Button/>
<main>
 
   
    <h1 class="h1" >Welcome , {user}</h1>
  </main>
{/if}
<style>
  .h1{
    position: absolute;
    top: 200px;
    left: 600px;
    font-size: 50px;
  }

</style>
