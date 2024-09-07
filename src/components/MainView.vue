<template>
<div>
    <div class="app-bar">
        <div class="logo">
            <img src="images/other/logo.png" alt="Logo">
        </div>
        <button class="hamburger" ref="hamburger" @click="toggleNav">&#9776;</button>
        <nav ref="nav" :class="['nav', { 'nav--open': isNavOpen }]">
            <button @click="scrollTo('home')">START</button>
            <button @click="scrollTo('about')">O MNIE</button>
            <button @click="scrollTo('skills')">UMIEJĘTNOŚCI</button>
            <button @click="scrollTo('projects')">PROJEKTY</button>
            <button @click="scrollTo('contact')">KONTAKT</button>
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
                <p>KONTAKT</p>
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
        },
        handleClickOutside(event) {
            if (this.isNavOpen && !this.$refs.nav.contains(event.target) && !this.$refs.hamburger.contains(event.target)) {
                this.isNavOpen = false;
            }
        }
    },
    mounted() {
        document.addEventListener('mousedown', this.handleClickOutside);
    },
    beforeUnmount() {
        document.removeEventListener('mousedown', this.handleClickOutside);
    }
}
</script>

<style>
body {
    background: linear-gradient(to right, #1c1c1c, #3a3a3a);
    margin: 0;
    font-family: 'Roboto', sans-serif;
}

.app-bar {
    position: fixed;
    width: 90%;
    top: 20px;
    left: 50%;
    transform: translateX(-50%);
    background: linear-gradient(to right, #1c1c1c, #3a3a3a);
    color: white;
    font-size: 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 30px;
    height: 70px;
    border-radius: 25px;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
    z-index: 99;
    transition: top 0.3s ease-in-out;
}

.logo img {
    height: 50px;
    margin-top: 5px;
}

.hamburger {
    display: none;
    background: none;
    border: none;
    color: white;
    font-size: 2em;
    cursor: pointer;
    transition: transform 0.3s ease, color 0.3s ease;
}

.hamburger:hover {
    transform: rotate(90deg);
    color: #7060D3;
}

.nav {
    display: flex;
    gap: 30px;
}

.nav button {
    background: none;
    border: none;
    color: white;
    font-size: 1.1em;
    padding: 10px 20px;
    cursor: pointer;
    border-radius: 15px;
    transition: background-color 0.3s ease, color 0.3s ease;
}

.nav button:hover {
    background-color: #7060D3;
    color: white;
}

@media (max-width: 768px) {
    .app-bar {
        width: 80%;
        padding: 0 20px;
    }

    .nav {
        flex-direction: column;
        position: absolute;
        top: 80px;
        right: 0;
        background: linear-gradient(to right, #1c1c1c, #3a3a3a);
        width: 100%;
        max-height: 0;
        opacity: 0;
        overflow: hidden;
        transition: max-height 0.3s ease, opacity 0.3s ease;
        border-radius: 25px;
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
    font-family: 'Roboto', sans-serif;
}

.footer-content {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
}

.footer-left,
.footer-right {
    flex: 1;
    padding: 20px;
}

.footer-left {
    background-color: #7060D3;
}

.footer-right {
    margin: 0;
    max-width: 30%;
    background: linear-gradient(to right, #1c1c1c, #3a3a3a);
    text-align: left;
}

.footer a {
    color: white;
    text-decoration: none;
}

.footer a:hover {
    text-decoration: underline;
}

@media (max-width: 768px) {
    .footer-content {
        flex-direction: column;
    }

    .footer-left {
        background-color: #7060D3;
        text-align: center;
    }

    .footer-right {
        max-width: 100%;
        background-color: #343B45;
        text-align: center;
    }
}
</style>
