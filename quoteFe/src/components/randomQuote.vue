<template>
    <div class="quote-container">
      <div v-if="quote" class="quote">
        "{{ quote }}"
      </div>
      <button @click="fetchQuote">New Reflection</button>
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
    max-width: 600px;
    text-align: center;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  .quote {
    font-size: 1.5em;
    font-style: italic;
    margin-bottom: 20px;
    color: #3e3e3e; /* Soft dark color for the quote text */
  }
  
  button {
    background-color: #b5a998; /* Muted brown for a natural feel */
    color: #f4f1ed;
    font-family: "Georgia", serif;
    font-size: 1em;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  button:hover {
    background-color: #a49582; /* Slightly darker on hover */
  }
  
  button:focus {
    outline: none;
  }
  
  button:active {
    background-color: #8a7c70;
  }
  </style>
  