<template>
    <div class="not-found">
      <img 
        src="/src/assets/404-illustration.svg" 
        alt="Page non trouvée"
        class="not-found-image"
      >
      <h1>404</h1>
      <p>La page que vous recherchez n'existe pas</p>
      <router-link to="/" class="home-link">
        Retour à l'accueil
      </router-link>
    </div>
  </template>
    
    <script>
    </script>

<style scoped>
  .not-found {
    min-height: calc(100vh - 160px);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 2rem;
    text-align: center;
  }
  
  .not-found-image {
    max-width: 400px;
    width: 100%;
    height: auto;
    margin-bottom: 2rem;
  }
  
  h1 {
    font-size: 6rem;
    color: #333;
    margin: 0;
  }
  
  p {
    font-size: 1.5rem;
    color: #666;
    margin: 1rem 0 2rem;
  }
  
  .home-link {
    display: inline-block;
    padding: 0.75rem 2rem;
    background-color: red;
    color: white;
    text-decoration: none;
    border-radius: 4px;
    transition: background-color 0.3s ease;
  }
  
  .home-link:hover {
    background-color: red;
  }
  
  </style>
