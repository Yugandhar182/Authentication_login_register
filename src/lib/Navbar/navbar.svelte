<script>
    import { Navbar, NavBrand, NavLi, NavUl, NavHamburger } from 'flowbite-svelte';
    import { goto } from '$app/navigation';
    
    import {  Dropdown, DropdownItem,  } from 'flowbite-svelte';
    
   let  user = null;
    let showModal = false;
  
    function openModal() {
      showModal = true;
    }
  
    function closeModal() {
      showModal = false;
    }



  function candidatelist() {
    goto('/candidatelist');
   
  }
  function joblist() {
    goto('/joblist');
   
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
    
    let isNavbarVisible = false;
  
    function toggleNavbar() {
      isNavbarVisible = !isNavbarVisible;
    }
  </script>
  
  <Navbar style="background-color: blue;" let:hidden let:toggle>
    <NavBrand href="/">
    </NavBrand>
    <NavHamburger on:click={toggle} />
    <NavUl {hidden}>
      <li>
        <img src="https://i.stack.imgur.com/YQu5k.png" alt="Profile Image" class="nav-image" style="margin-top: auto; cursor:pointer" on:click={openModal} />
      </li>
    </NavUl>
  </Navbar>

 
  <Dropdown style="position: absolute; top: 10%; left: 50%; width: 20%; margin-left: 500px" >
    <div slot="header" class="px-12 py-2">
      <span class="block truncate text-sm font-medium" style="color: crimson; font-size: large">Hire Optica</span>
    </div>
    <DropdownItem style="font-size: 15px; " on:click={Businessprofile}>Business Profile</DropdownItem>
    <DropdownItem style="font-size: 15px; " slot="footer" on:click={handleLogout}>Logout</DropdownItem>
  </Dropdown>
  

  
  <div class="vertical-navbar">
    <Navbar style="background-color: blue;">
      <NavHamburger on:click={toggleNavbar} />
      <NavUl>
        <li>
          <div class="mb-6">
            <i class="fa fa-mortar-board" on:click={candidatelist} style="font-size: 24px; color: white; margin-top: 125px; cursor:pointer; margin-left:-28px">Candidates</i>
          </div>
          <div class="mb-6">
            <i class="fa fa-briefcase" on:click={joblist} style="font-size: 26px; color: white; margin-top: 10px; margin-left:-28px; cursor:pointer;" >Jobs</i>
          </div>
        </li>
      </NavUl>
    </Navbar>
  
  </div>
 
  <style>
    .navbar {
      background-color: blue;
      color: white;
    }
  
    .nav-image {
      width: 50px; /* Set the desired width for your image */
      height: 54px; /* Set the desired height for your image */
      margin-right: 8px; /* Add some spacing between the image and text */
    }
  
    .vertical-navbar {
      position: fixed;
      top: 0;
      left: 0;
      width: 150px; /* Set the desired width for your vertical navbar */
      height: 100%; /* Make the navbar cover the entire height of the viewport */
      background-color: blue;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
    }
   

    .dropdown {
    width: 25%;
  }

  @media screen and (max-width: 768px) {
    /* Adjust width for screens up to 768px */
    .dropdown {
      width: 50%;
    }
  }

  @media screen and (max-width: 480px) {
    /* Adjust width for screens up to 480px */
    .dropdown {
      width: 75%;
    }
  }

  </style>
  