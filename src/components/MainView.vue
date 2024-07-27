<template>
    <div>
        <div class="app-bar">
            <div class="logo"></div>
            <button class="hamburger" @click="toggleNav">&#9776;</button>
            <nav :class="{ 'nav': true, 'nav--open': isNavOpen }">
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
    data() {
        return {
            isNavOpen: false
        };
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
                this.isNavOpen = false;
            }
        },
        toggleNav() {
            this.isNavOpen = !this.isNavOpen;
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

.hamburger {
    display: none;
    background: none;
    border: none;
    color: white;
    font-size: 1.5em;
    cursor: pointer;
    transition: transform 0.3s ease;
}

.hamburger:hover {
    transform: rotate(90deg);
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
    transition: background-color 0.3s ease, transform 0.2s ease;
}

.nav button:hover {
    color: #7060D3;
    transform: scale(1.1);
}

@media (max-width: 768px) {
    .nav {
        display: flex;
        flex-direction: column;
        position: absolute;
        top: 60px;
        right: 0;
        background-color: #222831;
        width: 100%;
        max-height: 0;
        opacity: 0;
        overflow: hidden;
        transition: max-height 0.3s ease, opacity 0.3s ease;
    }

    .nav--open {
        max-height: 500px;
        opacity: 1;
    }

    .hamburger {
        display: block;
    }

    .nav button {
        padding: 15px;
        transition: background-color 0.3s ease, transform 0.2s ease;
    }
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