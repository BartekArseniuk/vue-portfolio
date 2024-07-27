<template>
<div>
    <div class="app-bar">
        <div class="logo"></div>
        <nav class="nav">
            <button @click="scrollTo('home')">HOME</button>
            <button @click="scrollTo('about')">ABOUT ME</button>
            <button @click="scrollTo('skills')">SKILLS</button>
            <button @click="scrollTo('projects')">PROJECTS</button>
            <button @click="scrollTo('contact')">CONTACT</button>
        </nav>
    </div>

    <main>
        <section id="home">
            <HomeSection />
        </section>
        <section id="about">
            <AboutMeSection />
        </section>
        <section id="skills">
            <SkillsSection />
        </section>
        <section id="projects">
            <ProjectsSection />
        </section>
        <section id="contact">
            <ContactSection />
        </section>
    </main>
</div>
</template>

<script>
import HomeSection from './HomeSection.vue';
import AboutMeSection from './AboutMeSection.vue';
import SkillsSection from './SkillsSection.vue';
import ProjectsSection from './ProjectsSection.vue';
import ContactSection from './ContactSection.vue';

export default {
    components: {
        HomeSection,
        AboutMeSection,
        SkillsSection,
        ProjectsSection,
        ContactSection
    },
    methods: {
        scrollTo(sectionId) {
            const element = document.getElementById(sectionId);
            if (element) {
                const navBarHeight = document.querySelector('.app-bar').offsetHeight;
                window.scrollTo({
                    top: element.offsetTop - navBarHeight,
                    behavior: 'smooth'
                });
            }
        }
    }
}
</script>

<style>
body {
    background-color: #222831;
    margin: 0;
    font-family: Arial, sans-serif;
}

.app-bar {
    position: fixed;
    z-index: 99;
    top: 0;
    left: 0;
    right: 0;
    background-color: #222831;
    color: white;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;
    height: 60px;
    box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
}

.nav {
    display: flex;
    gap: 20px;
}

.nav button {
    background: none;
    border: none;
    color: white;
    font-size: 1em;
    padding: 10px;
    cursor: pointer;
    border-radius: 5px;
    transition: background-color 0.3s ease;
}

.nav button:hover {
    color: #7060D3;
}

section {
    width: 100%;
    margin: 0;
    color: white;
}

h1 {
    color: white;
}
</style>