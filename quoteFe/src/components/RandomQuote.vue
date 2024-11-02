<template>
    <div class="quote-container">
      <div v-if="quote" class="quote">
        {{ quote }}
      </div>
      <div  class="Author">
        {{ author }} - {{ book }}
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
    justify-content: center;
    align-items: center;
    height: 100vh;
    
  }
  
  .quote-container {
    background-color: #eae4d3; /* Off-white card background for a timeless feel */
    border: 1px solid #b5a998; /* Subtle border for structure */
    border-radius: 8px;
    padding: 20px;
    text-align: center;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
    flex-direction: column;
    
    
  }
  
  .quote {
    font-size: 1.5em;
    font-style: italic;
    color: #3e3e3e; /* Soft dark color for the quote text */
  }
  
  .Author{
    font-size: 1.25em;
    padding-top: 20px;
    color: #3e3e3e;
    
   
  }
  
  
  </style>
  