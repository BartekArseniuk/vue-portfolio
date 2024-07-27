<template>
<div>
    <div class="app-bar">
        <div class="logo"></div>
        <button class="hamburger" @click="toggleNav">&#9776;</button>
        <nav :class="['nav', { 'nav--open': isNavOpen }]">
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

    <footer class="footer">
        <div class="footer-content">
            <div class="footer-left">
                <p>Bartosz Arseniuk</p>
                <h4>początkujący programista</h4>
            </div>
            <div class="footer-right">
                <p>CONTACT</p>
                <p>Email: <a href="mailto:example@example.com">bartekarseniuk1701@gmail.com</a></p>
                <p>Telefon: <a href="tel:+48123456789">+48 508 471 740</a></p>
            </div>
        </div>
    </footer>
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
    z-index: 99;
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
    }
}

main section {
    width: 100%;
    margin: 0;
    color: white;
}

.footer {
    color: white;
    font-weight: bold;
    position: relative;
    text-align: left;
}

.footer-content {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
}

.footer-left,
.footer-right {
    flex: 1;
    padding: 10px;
}

.footer-left {
    background-color: #7060D3;
}

.footer-right {
    margin: 0;
    max-width: 350px;
    background-color: #343B45;
    text-align: left;
}

.footer a {
    color: white;
    text-decoration: none;
}

.footer a:hover {
    text-decoration: underline;
}
</style>