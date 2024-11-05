<template>
    <div class="Description">
      <div class="desc">
        <img class="img" v-bind:src=imglink>
        <div class ="bio">{{ bio }}</div> 
        <div class="break"></div>
        <div class = "links">
          <p v-for="(book,index) in books">
          BUY {{ book.name }} on <a v-bind:href=book.link> AMAZON</a>
          </p>
       </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    
    data() {
      return {
        
        bio: null,
        imglink : null,
        books: null,
      };
    },
    methods: {
      async fetchAuthor() {
        try {
          const response = await fetch('https://serverfibergo.onrender.com/author/');
          if (!response.ok) {
            throw new Error("Network response was not ok");
          }
          const data = await response.json();
          this.bio = data.bio
          this.imglink = data.imglink
          this.books = data.books
        } catch (error) {
          console.error("Error fetching the quote:", error);
        }
      }
    },
    created() {
      this.fetchAuthor();
    },
    
  };
  </script>
  
  <style scoped>
  /* Styling for a stoic aesthetic */
  
  
 
  
  .desc {
    font-family: "Georgia", serif;
    background-color: #f4f1ed; /* Soft beige background */
    color: #3e3e3e;
    display: grid;
    font-size: 1em;
    flex-direction: row;
    margin-bottom: 20px;
    color: #3e3e3e; /* Soft dark color for the quote text */
    flex-wrap:initial;
    
    text-align: justify;
    text-justify: inter-word;
  }

  .bio{
    grid-row: 1;
    font-family: "Georgia", serif;
    background-color: #f4f1ed; /* Soft beige background */
    color: #3e3e3e;
  }
 
  
  
  .img {
    grid-row: 1;
    padding-right: 10px;
    max-width: 150px;
    box-sizing: border-box;
    
    
  }

  .links{
    font-family: "Georgia", serif;
    background-color: #f4f1ed; /* Soft beige background */
    color: #3e3e3e;
    font-size: 1.5em;
    align-self: center;
    text-align: center;         
  display: flex;                
  flex-direction: column;      
  justify-content: center;     
  align-items: center; 
    
  }

  .links a {
    color: #b55b5b;
    text-decoration: none;
  }


  
  </style>
  