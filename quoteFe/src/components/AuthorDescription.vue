<template>
    <div class="Description">
      <div v-if="quote" class="desc">
        <img class="img" src ="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTOewZqrA4EpMIQQo3pOkIzTnkUN1hVQ1ZfNg&s">
        "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum."
      </div>
       
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        quote: null,
      };
    },
    methods: {
      async fetchQuote() {
        try {
          const response = await fetch('http://localhost:8080/quote/random');
          if (!response.ok) {
            throw new Error("Network response was not ok");
          }
          const data = await response.json();
          this.quote = data.quote;
          this.author = data.author;
          this.book = data.book;
        } catch (error) {
          console.error("Error fetching the quote:", error);
        }
      }
    },
    created() {
      this.fetchQuote();
    }
  };
  </script>
  
  <style scoped>
  /* Styling for a stoic aesthetic */
  
  body {
    font-family: "Georgia", serif;
    background-color: #f4f1ed; /* Soft beige background */
    color: #3e3e3e;            /* Dark grey text for readability */
    margin: 0;
    display: flex;
    justify-content:space-between;
    align-items: center;
   
  }
  
 
  
  .desc {
    font-size: 1em;
    flex-direction: row;
    margin-bottom: 20px;
    color: #3e3e3e; /* Soft dark color for the quote text */
    display: flex;
    justify-content:flex-end ;
  }
  
  
  
  .img {
    padding: 10px;
    width: 300px;
    box-sizing: border-box;
    
    
  }
  
  </style>
  