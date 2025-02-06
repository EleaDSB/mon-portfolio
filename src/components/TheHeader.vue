<template>
  <header class="header">
    <div class="logo" @click="scrollToTop">
      <img src="@/assets/EDS.png" alt="Logo personnel" />
    </div>
    <h2> Bienvenue sur mon portfolio</h2>
    <nav>
      <ul>
        <li><a href="#presentation" :class="{ active: activeSection === 'presentation' }">Présentation</a></li>
        <li><a href="#creations" :class="{ active: activeSection === 'creations' }">Créations</a></li>
        <li><a href="#contact" :class="{ active: activeSection === 'contact' }">Contact</a></li>
      </ul>
    </nav>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const activeSection = ref('presentation')

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}

const updateActiveSection = () => {
  const sections = ['presentation', 'creations', 'contact']
  const scrollPosition = window.scrollY

  for (const section of sections) {
    const element = document.getElementById(section)
    if (element) {
      const { offsetTop, offsetHeight } = element
      if (scrollPosition >= offsetTop - 100 && 
          scrollPosition < offsetTop + offsetHeight - 100) {
        activeSection.value = section
        break
      }
    }
  }
}

onMounted(() => {
  window.addEventListener('scroll', updateActiveSection)
})

onUnmounted(() => {
  window.removeEventListener('scroll', updateActiveSection)
})
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px 30px;
  background-color: white;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  z-index: 1000;
}

.logo {
  cursor: pointer;
}

h2 {
  padding-left: 175px;
  color: red;
}

.logo img {
  height: 50px;
  border-radius: 50%;
  width: auto;
}

nav ul {
  display: flex;
  gap: 2rem;
  list-style: none;
  margin: 0;
  padding: 0;
}

nav a {
  text-decoration: none;
  color: red;
  font-weight: 500;
  padding-bottom: 0.25rem;
  position: relative;
}

nav a.active::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 100%;
  height: 2px;
  background-color: currentColor;
}
</style>