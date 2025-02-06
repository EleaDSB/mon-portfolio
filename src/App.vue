<script setup>
import { ref } from 'vue'
import { RouterView } from 'vue-router'
import TheHeader from './components/TheHeader.vue'
import TheFooter from './components/TheFooter.vue'
import ProjectModal from './components/ProjectModal.vue'

// État du modal
const isModalOpen = ref(false)
const selectedProject = ref(null)

// Fonctions pour gérer le modal
const openProjectModal = (project) => {
  selectedProject.value = project
  isModalOpen.value = true
}

const closeModal = () => {
  isModalOpen.value = false
  selectedProject.value = null

const myemail = import.meta.env
}
</script>

<template>
  <div class="app">
    <TheHeader />
    <main>
      <RouterView @openProject="openProjectModal" />
    </main>
    <TheFooter />
    
    <ProjectModal
      :is-open="isModalOpen"
      :project="selectedProject"
      @close="closeModal"
    />
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
  min-height: 100vh;
}

.app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

main {
  margin-top: 80px;
  flex: 1;
}
</style>