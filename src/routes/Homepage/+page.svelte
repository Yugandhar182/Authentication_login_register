<script>
  import Button from "$lib/Navbar/navbar.svelte";
  import { auth } from '$lib/firebase/firebase.js';
  import { onMount } from 'svelte';
  import { goto } from '$app/navigation';

  let isAuthenticated = false; // Initialize a loading state

  // Check if the user is authenticated when the component mounts
  onMount(async () => {
    // Check if the user is authenticated
    if (auth.currentUser) {
      isAuthenticated = true; // User is authenticated
    } else {
      // If the user is not authenticated, redirect them to the login page
      goto('/'); 
    }
  });
</script>
{#if isAuthenticated}
<Button/>
<main>
 
    <!-- Protected content that should only be shown when authenticated -->
    <h1 class="h1" style="color:red;">Welcome to Hire optica</h1>
    <div class="container">
 
    </div>
 
 
  

 
</main>
{/if}
<style>
  .h1{
    position: absolute;
    top: 200px;
    left: 600px;
    font-size: 80px;
  }
</style>
