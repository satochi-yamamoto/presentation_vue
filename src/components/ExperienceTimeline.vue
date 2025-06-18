<script setup>
import { ref, onMounted } from 'vue'
import experienceData from '../data/experience'
import { useScrollAnimation } from '../composables/useScrollAnimation'

const { animateOnScroll } = useScrollAnimation()
const experiences = ref(experienceData)

onMounted(() => {
  animateOnScroll()
  window.addEventListener('scroll', animateOnScroll)
})
</script>

<template>
  <section id="experience" class="section">
    <div class="container">
      <h2 class="section-title">Experiência Profissional</h2>
      
      <div class="timeline">
        <div 
          v-for="(exp, index) in experiences" 
          :key="exp.id"
          class="timeline-item"
          :class="{ 'left': index % 2 === 0, 'right': index % 2 !== 0 }"
        >
          <div class="timeline-date">{{ exp.period }}</div>
          <div class="timeline-content">
            <h3>{{ exp.company }}</h3>
            <h4>{{ exp.position }}</h4>
            <p>{{ exp.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.timeline {
  position: relative;
  max-width: 800px;
  margin: 0 auto;
  padding: 40px 0;
}

.timeline::before {
  content: '';
  position: absolute;
  width: 2px;
  background: var(--secondary-color);
  top: 0;
  bottom: 0;
  left: 50%;
  margin-left: -1px;
}

.timeline-item {
  padding: 20px 40px;
  position: relative;
  width: 50%;
  box-sizing: border-box;
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.5s ease, transform 0.5s ease;
}

.timeline-item.visible {
  opacity: 1;
  transform: translateY(0);
}

.timeline-item.left {
  left: 0;
  text-align: right;
  padding-right: 70px;
}

.timeline-item.right {
  left: 50%;
  text-align: left;
  padding-left: 70px;
}

.timeline-date {
  font-weight: 600;
  color: var(--secondary-color);
  margin-bottom: 10px;
}

.timeline-content {
  background: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
}

.timeline-content h3 {
  margin-bottom: 5px;
  color: var(--dark-color);
}

.timeline-content h4 {
  margin-bottom: 10px;
  color: var(--secondary-color);
  font-weight: 500;
}

.timeline-item::after {
  content: '';
  position: absolute;
  width: 20px;
  height: 20px;
  background: var(--secondary-color);
  border-radius: 50%;
  top: 30px;
}

.timeline-item.left::after {
  right: -10px;
}

.timeline-item.right::after {
  left: -10px;
}

@media (max-width: 768px) {
  .timeline::before {
    left: 30px;
  }
  
  .timeline-item {
    width: 100%;
    padding-left: 70px;
    padding-right: 0;
    text-align: left;
  }
  
  .timeline-item.left,
  .timeline-item.right {
    left: 0;
    text-align: left;
    padding-right: 0;
    padding-left: 70px;
  }
  
  .timeline-item::after {
    left: 20px !important;
  }
}
</style>
