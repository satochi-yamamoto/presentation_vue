<script setup>
defineProps({
  scrolled: Boolean
})

const navItems = [
  { id: 'about', label: 'Sobre' },
  { id: 'experience', label: 'Experiência' },
  { id: 'projects', label: 'Projetos' },
  { id: 'skills', label: 'Habilidades' },
  { id: 'contact', label: 'Contato' }
]

const scrollTo = (id) => {
  const element = document.getElementById(id)
  if (element) {
    window.scrollTo({
      top: element.offsetTop - 80,
      behavior: 'smooth'
    })
  }
}
</script>

<template>
  <header :class="{ 'scrolled': scrolled }">
    <div class="container">
      <a href="#" class="logo" @click.prevent="scrollTo('home')">AY</a>
      <nav>
        <ul>
          <li v-for="item in navItems" :key="item.id">
            <a href="#" @click.prevent="scrollTo(item.id)">{{ item.label }}</a>
          </li>
        </ul>
      </nav>
      <a href="#" class="btn btn-outline">Currículo</a>
    </div>
  </header>
</template>

<style scoped>
header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  background: rgba(255, 255, 255, 0.95);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

header.scrolled {
  background: rgba(255, 255, 255, 0.98);
  padding: 10px 0;
}

.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 0;
}

.logo {
  font-family: var(--font-heading);
  font-size: 1.8rem;
  font-weight: 700;
  color: var(--primary-color);
  text-decoration: none;
}

nav ul {
  display: flex;
  list-style: none;
  gap: 30px;
}

nav a {
  text-decoration: none;
  color: var(--text-color);
  font-weight: 600;
  transition: color 0.3s ease;
}

nav a:hover {
  color: var(--secondary-color);
}
</style>
