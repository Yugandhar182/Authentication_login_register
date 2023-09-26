<script>
    import { goto } from '$app/navigation';
    import { auth } from '$lib/firebase/firebase.js';
    import { Button, Dropdown, DropdownItem,  } from 'flowbite-svelte';
    
    let showModal = false;
  
    function openModal() {
      showModal = true;
    }
  
    function closeModal() {
      showModal = false;
    }

  
    async function handleLogout() {
  try {
    const confirmation = confirm("Are you sure you want to log out?");
    
    // Check if the user confirmed (clicked "OK")
    if (confirmation) {
      // Remove user data from localStorage
      localStorage.removeItem('user');
  
      // Redirect to the login page
      goto('/');
    }
  } catch (error) {
    console.error("Error logging out:", error.message);
  }
}
 
  
    function Businessprofile() {
      goto('/businessprofile');
    }
  </script>
   
  <img class="imag" src="https://i.stack.imgur.com/YQu5k.png" alt="Click me" on:click={openModal} />
  
   <Dropdown style="height: 200px; width:200px" >
          <div slot="header" class="px-12 py-2">
           
            <span class="block truncate text-sm font-medium"  style="color: crimson; font-size:large">Hire Optica</span>
          </div>
          <DropdownItem  style="font-size:15px"  on:click={Businessprofile} >Business Profile</DropdownItem>
        
        
          <DropdownItem  slot="footer" on:click={handleLogout} >Logout</DropdownItem>
         
        </Dropdown>
 

  
  <style>
   .imag {
    position: absolute;
    top: 10px;
    right: 25px;
    height: 50px;
  }
 

 
  </style>
  