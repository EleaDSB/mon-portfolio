<template>
  <div class="project-card" @click="handleClick">
    <img 
      :src="project.thumbnail" 
      :alt="project.title"
      class="project-image"
    >
    <div class="project-info">
      <h3 class="project-title">{{ project.title }}</h3>
      <div class="project-technologies">
        <span 
          v-for="tech in project.technologies.slice(0, 3)" 
          :key="tech" 
          class="tech-tag"
        >
          {{ tech }}
        </span>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  project: {
    type: Object,
    required: true
  }
})

const emit = defineEmits(['projectClick'])

const handleClick = () => {
  emit('projectClick', props.project)
}
</script>

<style scoped>
.project-card {
  background: white;
  border-radius: 8px;
  overflow: hidden;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.project-card:hover {
  box-shadow: 4px 4px 8px rgba(0, 0, 0, 0.2);
  transform: translateY(-2px);
}

.project-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.project-info {
  padding: 1rem;
}

.project-title {
  margin-bottom: 0.5rem;
  color: #333;
  font-size: 1.2rem;
}

.project-technologies {
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
}

.tech-tag {
  background-color: #f0f0f0;
  padding: 0.25rem 0.75rem;
  border-radius: 15px;
  font-size: 0.8rem;
  color: black;
}
</style>