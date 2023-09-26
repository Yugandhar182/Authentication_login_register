<script>
  import { auth } from '$lib/firebase/firebase.js';
  import { onMount } from 'svelte';
  import { goto } from '$app/navigation';
  import { Card } from 'flowbite-svelte';


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
<div class="card-container">
  <Card  class="card">
    <h1 class="mb-2 text-2xl font-bold tracking-tight text-green-500 dark:text-white">
      Congratulations! You have successfully signed in to your account. Please go to the Login page.
    </h1>
    
    <a href="/" style="color: blue; font-weight: bold; font-size: 28px;" class="h2">Login</a>
  </Card>
</div>
{/if}

<style>
  /* Center the card in the middle of the page */
  .card-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh; /* Ensure the card fills the entire viewport height */
    color: darkgreen;
  }

  .h2 {
    font-weight: bold;
    font-size: 70px;
    margin-top: 20px; /* Adjust as needed */
  }

  .h1 {
    font-weight: normal;
    font-size: 20px;
    text-align: center; /* Center-align the text */
    margin-top: 20px; /* Adjust as needed */
  }
</style>

