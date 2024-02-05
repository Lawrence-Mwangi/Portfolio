<script setup>
import Navbar from '../components/NavbarComponent.vue'
import Footer from '../components/FooterComponent.vue'
import Hero from './HeroView.vue'
import About from './AboutView.vue'
import Skill from './SkillsView.vue'
import Service from './ServicesView.vue'
import Work from './Workview.vue'
import Blog from './BlogView.vue'
</script>

<template>
    <Navbar/>
    <section class="container" id="home" >
        <Hero/>
    </section>

    <section class="container" id="about"  v-motion-pop-visible>
        <About/>
    </section>

    <section class="container" id="skills"  v-motion-pop-visible>
        <Skill/>
    </section>

    <section class="container" id="services"  v-motion-pop-visible>
        <Service/>
    </section>
    
    <section class="container " id="work"  v-motion-pop-visible>
        <Work/>
    </section>
    
    <section class="container" id="blog"  v-motion-pop-visible>
        <Blog/>
    </section>

    <Footer/>
</template>

  