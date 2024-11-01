<template>
    <nav class="navbar">
      <div class="nav-title">Stoic Reflections</div>
      <ul class="nav-links">
        <li><a href="#">Home</a></li>
        <li><a href="#">Quotes</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Contact</a></li>
      </ul>
    </nav>
  </template>
  
  <script>
  export default {
    name: 'NavBar',
  };
  </script>
  
  <style scoped>
  /* Navbar styling for a stoic theme */
  
  .navbar {
    position: fixed;            /* Fixes navbar at the top */
    top: 0;
    left: 0;
    right: 0;
    height: 60px;
    background-color: #eae4d3;  /* Soft, calm background color */
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 30px;
    border-bottom: 1px solid #b5a998; /* Subtle border for structure */
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1); /* Soft shadow for slight elevation */
    z-index: 1000; /* Ensures navbar stays above other content */
  }
  
  .nav-title {
    font-family: "Georgia", serif;
    font-size: 1.5em;
    color: #3e3e3e; /* Dark color for the title text */
  }
  
  .nav-links {
    list-style: none;
    display: flex;
    gap: 20px;
    margin: 0;
    padding: 0;
  }
  
  .nav-links li {
    font-family: "Georgia", serif;
  }
  
  .nav-links a {
    color: #3e3e3e;
    text-decoration: none;
    font-size: 1em;
    transition: color 0.3s ease;
  }
  
  .nav-links a:hover {
    color: #8a7c70; /* Subtle color change on hover */
  }
  </style>
  