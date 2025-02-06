<template>
  <div class="home">
    <!-- Section Présentation -->
    <section id="presentation" class="section">
      <h1>Bonjour, je suis Eléa DE SOUSA</h1>
      <p class="intro">
Actuellement en formation de développement web dans le cadre d’une reconversion professionnelle, je suis passionnée par le monde du numérique et de la création de solutions innovantes. Cette démarche reflète mon envie d’apprendre, de relever de nouveaux défis, et de construire des projets alliant technique et créativité. <br>
<br>
Avec mon parcours précédent, j’apporte une perspective unique et des compétences transférables que je souhaite mettre à profit dans le domaine du web. Mon objectif est de maîtriser les technologies actuelles et de contribuer activement à des projets ambitieux. <br>
<br>
Ce site a été conçu pour vous permettre de découvrir mes créations et d’explorer les projets sur lesquels j’ai travaillé. Si vous êtes intéressé(e) par une collaboration ou souhaitez simplement en savoir plus, n’hésitez pas à me contacter via la section dédiée.</p>

<img src="/src/assets/EDS.png" alt="logo site">

    </section>

    <!-- Section Créations -->
    <section id="creations" class="section">
      <h2>Mes Créations</h2>
      <div class="projects-grid">
        <ProjectCard
          v-for="project in projects"
          :key="project.id"
          :project="project"
          @click="$emit('open-project', project)"
        />
      </div>
    </section>

    <!-- Section Contact -->
    <section id="contact" class="section">
      <h2>Me Contacter</h2>
      <form @submit.prevent="handleSubmit" class="contact-form">
        <div class="form-group">
          <label for="name">Nom et prénom</label>
          <input 
            type="text" 
            id="name" 
            v-model="form.name" 
            required
          />
        </div>

        <div class="form-group">
          <label for="object">Objet</label>
          <input 
            type="text" 
            id="object" 
            v-model="form.object" 
            required
          />
        </div>

        <div class="form-group">
          <label for="message">Message</label>
          <textarea 
            id="message" 
            v-model="form.message" 
            required
          ></textarea>
        </div>

        <button type="submit" class="submit-button">Envoyer</button>
      </form>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import ProjectCard from '../components/ProjectCard.vue'

// Données des projets
const projects = ref([
  {
    id: 1,
    title: 'Création de mon CV en HTML et en CSS',
    thumbnail: '/src/assets/CVCut.png',
    date: '2024-06-18',
    technologies: ['VSCODE','CSS', 'HTML'],
    description: 'CV créer en utilisant HTML et CCS, présentant mes compétences et projets.',
    githubUrl: 'https://github.com/EleaDSB/Mon_cv',
    images: [
      { url: '/src/assets/moncv.png', alt: 'Vue du CV' },
    ]
  },
  {
    id: 2,
    title: 'Rédaction d\'un cahier des charges',
    thumbnail: '/src/assets/CDCCut.png',
    date: '2024-10-03',
    technologies: ['Pack office',],
    description: 'rédaction d\'un cahier des charges pour un site de vente en ligne',
    pdfUrl: '/src/assets/Cahier-Des-Charges.pdf',
    images: [
      { url: '/src/assets/CDCCut.png', alt: 'Extrait 1 du cahier des charges' },
      { url: '/src/assets/CDCCut2.png', alt: 'Extrait 2 du cahier des charges' }
    ]
  },
  {
    id: 3,
    title: 'Dynamiser un espace commentaire',
    thumbnail: '/src/assets/Espace-Co.png',
    date: '2024-12-13',
    technologies: ['VSCODE', 'JavaScript'],
    description: 'Application météo avec affichage des prévisions en temps réel.',
    githubUrl: 'https://github.com/EleaDSB/dynamiser-espace-commentaire',
    images: [
      { url: '/src/assets/Espace-Co.png', alt: 'Extrait du site' },
    ]
  }
])

// État du formulaire
const form = ref({
  name: '',
  object: '',
  message: ''
})

// Gestion du formulaire
const handleSubmit = async () => {
  try {
    console.log('Form submitted:', form.value)
    form.value = {
      name: '',
      object: '',
      message: ''
    }
  } catch (error) {
    console.error('Error submitting form:', error)
  }
}
//TEST
console.log(import.meta.env.VITE_EMAIL_DESTINATION)
//END TEST
</script>

<style scoped>
.home {
  display: flex;
  flex-direction: column;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 100px;
}

img{
  max-height: 30%;
  max-width: 30%;
  border-radius: 50%;

}
.section {
  width: 100%;
  padding: 4rem 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 1.5rem;
  width: 100%;
  text-align: center;
}

h2 {
  font-size: 2rem;
  margin-bottom: 2.5rem;
  width: 100%;
  text-align: center;
}

.intro {
  font-size: 1.2rem;
  color: #666;
  max-width: 600px;
  margin: 0 auto 2rem;
  line-height: 1.6;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  width: 100%;
  max-width: 1200px;
}

.contact-form {
  width: 100%;
  max-width: 600px;
  margin: 0 auto;
}

.form-group {
  margin-bottom: 1.5rem;
  text-align: left;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  color: white;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 1rem;
}

.form-group textarea {
  min-height: 150px;
  resize: vertical;
}

.submit-button {
  background-color: red;
  color: white;
  padding: 0.75rem 2rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s ease;
  margin: 0 auto;
  display: block;
}

.submit-button:hover {
  background-color: orangered;
}

</style>