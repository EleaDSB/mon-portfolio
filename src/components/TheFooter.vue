<template>
  <footer class="footer">
    <div class="social-links">
      <a 
        href="https://github.com/EleaDSB" target="_blank">
        <img class="logo" src="/src/assets/icons8-github-50.png" alt="logo du Linkedin">
      </a>

      <a 
        href="https://www.linkedin.com/in/el%C3%A9a-bitsch-6a74841b2/" target="_blank" >
          <img class="logo" src="/src/assets/icons8-linkedin-50.png" alt="logo de GitHub">
       </a>
    </div>

    <div class="update-info">
      Dernière mise à jour : {{ lastUpdateDate }}
    </div>
  </footer>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const formatDate = (date) => {
  return new Intl.DateTimeFormat('fr-FR', {
    day: 'numeric',
    month: 'long',
    year: 'numeric'
  }).format(date)
}

const lastUpdateDate = ref(formatDate(new Date()))
</script>

<style>
.footer {
  background-color: #f8f9fa;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.social-links {
  display: flex;
  align-items: center;
}

.icon {
  width: 20px;
  height: 20px;
  transition: color 0.3s ease;
}

.social-links a {
  color: #666;
  transition: color 0.3s ease;
}

.social-links a:hover {
  color: #f30606;
}

.update-info {
  font-size: 14px;
  color: #666;
}

</style>