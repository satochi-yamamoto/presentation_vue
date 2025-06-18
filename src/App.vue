<script setup>
import { ref, onMounted } from 'vue'
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ExperienceTimeline from './components/ExperienceTimeline.vue'
import ProjectsGrid from './components/ProjectsGrid.vue'
import SkillsChart from './components/SkillsChart.vue'
import ContactForm from './components/ContactForm.vue'

const currentYear = ref(new Date().getFullYear())
const scrolled = ref(false)

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

const handleScroll = () => {
  scrolled.value = window.scrollY > 100
}
</script>

<template>
  <NavBar :scrolled="scrolled" />
  <main>
    <HeroSection id="home" />
    <AboutSection id="about" />
    <ExperienceTimeline id="experience" />
    <ProjectsGrid id="projects" />
    <SkillsChart id="skills" />
    <ContactForm id="contact" />
  </main>
  <footer>
    <div class="container">
      <p>&copy; {{ currentYear }} Alex Yamamoto. Todos os direitos reservados.</p>
    </div>
  </footer>
</template>

<style scoped>
footer {
  background: var(--dark-color);
  color: white;
  padding: 2rem 0;
  text-align: center;
}
</style>
