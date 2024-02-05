<script setup>
    import { ref, onMounted, onBeforeUnmount } from 'vue';

    const sections = ref([
    { id: 'home', label: 'Home', isActive: false },
    { id: 'about', label: 'About', isActive: false },
    { id: 'skills', label: 'Skills', isActive: false },
    { id: 'work', label: 'Work', isActive: false },
    { id: 'blog', label: 'Blog', isActive: false },
    ]);

    const isMenuOpen = ref(false);

    const navigate = (sectionId) => {
    const targetElement = document.getElementById(sectionId);
    if (targetElement) {
        window.scrollTo({
        top: targetElement.offsetTop,
        behavior: 'smooth',
        });
    }
    // Close the menu on navigation
    isMenuOpen.value = false;
    };

    const toggleMenu = () => {
    isMenuOpen.value = !isMenuOpen.value;
    };

    const updateActiveState = () => {
    const scrollPosition = window.scrollY;
    sections.value.forEach((section) => {
        const targetElement = document.getElementById(section.id);
        if (targetElement) {
        const offsetTop = targetElement.offsetTop;
        const offsetBottom = offsetTop + targetElement.offsetHeight;
        section.isActive = scrollPosition >= offsetTop && scrollPosition < offsetBottom;
        }
    });
    };

    onMounted(() => {
    updateActiveState();
    window.addEventListener('scroll', updateActiveState);
    });

    onBeforeUnmount(() => {
    window.removeEventListener('scroll', updateActiveState);
    });

</script>



<template>
  <div class="nav_content">
    <div class="nav-container">
      <span class="logo">
        <a @click.prevent="navigate('home')" href="#">Lawrence</a>
      </span>

      <!-- Burger menu icon for mobile -->
      <div class="burger-menu" @click="toggleMenu">
        <span :class="{ 'line-1': !isMenuOpen }"></span>
        <span :class="{ 'line-2': !isMenuOpen }"></span>
        <span :class="{ 'line-3': !isMenuOpen }"></span>
      </div>

      <ul :class="{ 'show-menu': isMenuOpen }">
        <li v-for="(section, index) in sections" :key="index" :class="{ active: section.isActive }">
          <a @click.prevent="navigate(section.id)" href="#">{{ section.label }}</a>
        </li>
      </ul>
    </div>
  </div>
</template>

  
  
