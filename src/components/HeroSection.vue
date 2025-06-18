<script setup>
import { onMounted } from 'vue'
import { useScrollAnimation } from '../composables/useScrollAnimation'

const { animateOnScroll } = useScrollAnimation()

onMounted(() => {
  animateOnScroll()
  window.addEventListener('scroll', animateOnScroll)
})
</script>

<template>
  <section class="hero">
    <div class="container">
      <div class="hero-content">
        <h1>Alex Yamamoto</h1>
        <h2>Especialista em Marketing e Gestão de Projetos</h2>
        <p>+15 anos de experiência liderando equipes e projetos em grandes agências de comunicação</p>
        <div class="hero-cta">
          <a href="#contact" class="btn btn-primary">Entre em Contato</a>
          <a href="#experience" class="btn btn-outline">Ver Experiência</a>
        </div>
      </div>
      <div class="hero-image">
        <img src="../assets/images/avatar.jpg" alt="Alex Yamamoto">
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  height: 100vh;
  display: flex;
  align-items: center;
  background: linear-gradient(135deg, var(--light-color) 0%, #fff 100%);
  padding-top: 80px;
}

.container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 40px;
}

.hero-content {
  flex: 1;
}

.hero-content h1 {
  font-family: var(--font-heading);
  font-size: 3.5rem;
  margin-bottom: 20px;
  color: var(--dark-color);
}

.hero-content h2 {
  font-size: 1.5rem;
  font-weight: 400;
  margin-bottom: 20px;
  color: var(--text-light);
}

.hero-content p {
  margin-bottom: 30px;
  font-size: 1.1rem;
  max-width: 600px;
}

.hero-cta {
  display: flex;
  gap: 20px;
}

.hero-image {
  flex: 1;
  text-align: center;
}

.hero-image img {
  max-width: 100%;
  border-radius: 20px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

@media (max-width: 992px) {
  .container {
    flex-direction: column;
    text-align: center;
  }
  
  .hero-content {
    margin-bottom: 50px;
  }
  
  .hero-cta {
    justify-content: center;
  }
  
  .hero-image img {
    max-width: 80%;
  }
}

@media (max-width: 576px) {
  .hero-content h1 {
    font-size: 2.5rem;
  }
  
  .hero-content h2 {
    font-size: 1.2rem;
  }
  
  .hero-cta {
    flex-direction: column;
    gap: 15px;
  }
}
</style>
