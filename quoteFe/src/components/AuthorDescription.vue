<template>
    <div class="Description">
      <div class="desc">
        <img class="img" v-bind:src=imglink>
        <div class ="bio">{{ bio }}

          <div class = "links">
          <p v-for="(book,index) in books">
          BUY {{ book.name }} on <a v-bind:href=book.link > AMAZON</a>
          </p>
       </div>
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
          const response = await fetch('https://serverfibergo.onrender.com/author');
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
    /*
    font-family: "Georgia", serif;
    background-color: #FDF7E9; 
    color: #3e3e3e;
    display: grid;
    font-size: 1em;
    flex-direction: row;
    margin-bottom: 20px;
    color: #3e3e3e; 
    flex-wrap:initial;
    
    text-align: justify;
    text-justify: inter-word;
    */
    display:flex;
    background-color: #eae4d3; /* Off-white card background for a timeless feel */
    border: 1px solid #b5a998; /* Subtle border for structure */
    border-radius: 8px;
    padding: 20px;
    text-align: center;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
    flex-direction: row;
    width: auto;
    height: auto;
    padding-bottom: 20px;
  }

  .bio{
    grid-row: 1;
    font-family: "Georgia", serif;
    color: #3e3e3e;
    width: auto;
    height: auto;
  }

  
  
  .img {
    grid-row: 1;
    padding-right: 10px;
    max-width:150px;
 
    border-radius: 20px; 
  }

  .links{
    font-family: "Georgia", serif;
   
    color: #3e3e3e;
    font-size: 1.5em;
    align-self: center;
    text-align: center;         
  display: flex;                
  flex-direction: column;      
  justify-content: center;     
  align-items: center; 
  padding: 10px;   
  }

  .links a {
    color: #b55b5b;
    text-decoration: none;
  }

  @media (max-width: 800px) {
  .desc {
    
    display: block; 
  }

  .img {
    display: block;
       margin-left: auto;
      margin-right: auto;
  }
}

  
  </style>

  