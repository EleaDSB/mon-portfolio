<template>
    <Transition name="modal-fade">
      <div v-if="isOpen" class="modal-overlay" @click="closeModal">
        <div class="modal-content" @click.stop>
          <button class="modal-close" @click="closeModal" aria-label="Fermer">
            <svg width="24" height="24" viewBox="0 0 24 24">
              <path fill="currentColor" d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/>
            </svg>
          </button>
  
          <div class="modal-body">
            <h2 class="modal-title">{{ project.title }}</h2>
            
            <div class="project-date">
              Date de création : {{ formatDate(project.date) }}
            </div>
  
            <div class="project-technologies">
              <h3>Technologies utilisées :</h3>
              <div class="tech-tags">
                <span v-for="tech in project.technologies" 
                      :key="tech" 
                      class="tech-tag">
                  {{ tech }}
                </span>
              </div>
            </div>
  
            <div class="project-links">
              <a v-if="project.websiteUrl" 
                 :href="project.websiteUrl" 
                 target="_blank" 
                 rel="noopener noreferrer" 
                 class="project-link">
                Visiter le site
              </a>
              <a v-if="project.githubUrl" 
                 :href="project.githubUrl" 
                 target="_blank" 
                 rel="noopener noreferrer" 
                 class="project-link">
                Voir sur GitHub
              </a>
            </div>
  
            <div class="project-images">
              <img v-for="(image, index) in project.images"
                   :key="index"
                   :src="image.url"
                   :alt="image.alt"
                   class="project-image"
                   loading="lazy">
            </div>
          </div>
        </div>
      </div>
    </Transition>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue'
  
  const props = defineProps({
    isOpen: {
      type: Boolean,
      required: true
    },
    project: {
      type: Object,
      required: true,
      validator(project) {
        return project.title && project.date
      }
    }
  })
  
  const emit = defineEmits(['close'])
  
  const closeModal = () => {
    emit('close')
  }
  
  const formatDate = (date) => {
    return new Intl.DateTimeFormat('fr-FR', {
      day: 'numeric',
      month: 'long',
      year: 'numeric'
    }).format(new Date(date))
  }
  </script>
  
  <style scoped>
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.75);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
    padding: 20px;
  }
  
  .modal-content {
    background: white;
    border-radius: 8px;
    width: 100%;
    max-width: 800px;
    max-height: 90vh;
    position: relative;
    overflow-y: auto;
  }
  
  .modal-close {
    position: absolute;
    top: 1rem;
    right: 1rem;
    background: none;
    border: none;
    cursor: pointer;
    color: #666;
    padding: 4px;
    transition: color 0.3s ease;
  }
  
  .modal-close:hover {
    color: #333;
  }
  
  .modal-body {
    padding: 2rem;
  }
  
  .modal-title {
    font-size: 1.8rem;
    margin-bottom: 1rem;
    color: #333;
  }
  
  .project-date {
    color: #666;
    margin-bottom: 1.5rem;
  }
  
  .project-technologies {
    color: black;
    margin-bottom: 1.5rem;
  }
  
  .tech-tags {
    color: black;
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-top: 0.5rem;
  }
  
  .tech-tag {
    background-color: #f0f0f0;
    padding: 0.5rem 1rem;
    border-radius: 20px;
    font-size: 0.9rem;
  }
  
  .project-links {
    display: flex;
    gap: 1rem;
    margin-bottom: 1.5rem;
  }
  
  .project-link {
    display: inline-block;
    padding: 0.5rem 1rem;
    background-color: red;
    color: white;
    text-decoration: none;
    border-radius: 4px;
    transition: background-color 0.3s ease;
  }
  
  .project-link:hover {
    background-color: orangered;
  }
  
  .project-images {
    display: grid;
    gap: 1rem;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  }
  
  .project-image {
    width: 100%;
    height: auto;
    border-radius: 4px;
  }
  
  /* Animations */
  .modal-fade-enter-active,
  .modal-fade-leave-active {
    transition: opacity 0.3s ease;
  }
  
  .modal-fade-enter-from,
  .modal-fade-leave-to {
    opacity: 0;
  }
  
  </style>