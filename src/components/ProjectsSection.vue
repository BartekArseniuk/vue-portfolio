<template>
<div class="projects-section">
    <h2>PROJECTS</h2>
    <div class="project-buttons">
        <button class="project-button" :class="{ active: activeProject === 'DOG BREED IDENTIFICATION' }" @click="setActiveProject('DOG BREED IDENTIFICATION')">
            DOG BREED IDENTIFICATION
        </button>
        <button class="project-button" :class="{ active: activeProject === 'ESTIMATION APP' }" @click="setActiveProject('ESTIMATION APP')">
            ESTIMATION APP
        </button>
        <button class="project-button" :class="{ active: activeProject === 'AICADEMIA' }" @click="setActiveProject('AICADEMIA')">
            AICADEMIA
        </button>
        <button class="project-button" :class="{ active: activeProject === 'WEATHER APP' }" @click="setActiveProject('WEATHER APP')">
            WEATHER APP
        </button>
    </div>

    <transition name="fade" mode="out-in">
        <div :key="activeProject" class="project-details">
            <div v-show="activeProject === 'DOG BREED IDENTIFICATION'" class="project-content">
                <p>
                    Projekt zrealizowany w zespole 8 osób. Aplikacja mobilna rozpoznająca rasy psów z wykorzystaniem
                    modelu nauczania maszynowego. Uczestniczyłem w tworzeniu aplikacji na platformie Android w
                    języku Java z wykorzystaniem wzorca projektowego MVVM.
                </p>
                <img :src="dogBreedIdentificationImage.src" :alt="dogBreedIdentificationImage.alt" class="project-image" />
            </div>

            <div v-show="activeProject === 'ESTIMATION APP'" class="project-content">
                <p>
                    Aplikacja webowa pozwalająca na zarządzanie projektami klientów oraz ich wycenami. Back-end stworzony na Laravel'u, natomiast Front-end wykorzystuje VueJS oraz Vuetify Material Design.
                </p>
                <div class="carousel">
                    <button class="carousel-arrow left" @click="prevImage">‹</button>
                    <transition name="carousel-fade" mode="out-in">
                        <img v-if="currentImage" :key="currentImage.src" :src="currentImage.src" :alt="currentImage.alt" class="carousel-image" />
                    </transition>
                    <button class="carousel-arrow right" @click="nextImage">›</button>
                </div>
                <div class="carousel-dots">
                    <span v-for="(image, index) in estimationAppImages" :key="index" :class="{ active: index === currentImageIndex }" class="dot" @click="setImageIndex(index)"></span>
                </div>
            </div>

            <div v-show="activeProject === 'AICADEMIA'" class="project-content">
                <p>
                    Webowa gra edukacyjna skierowana do najmłodszych i nie tylko. Pozwala ona uczyć się nowych słów z języka angielskiego. Dobór poziomu słownictwa wybiera sam użytkownik — od A1 do C2. Każdego dnia losowane są nowe słowa oraz role postaci, które spotykamy na wyspie. Po rozmowach z mieszkańcami wyspy użytkownik może sprawdzić swoją wiedzę w walce z bossem w formie testu.
                </p>
                <div class="carousel">
                    <button class="carousel-arrow left" @click="prevImage">‹</button>
                    <transition name="carousel-fade" mode="out-in">
                        <img v-if="currentImage" :key="currentImage.src" :src="currentImage.src" :alt="currentImage.alt" class="carousel-image" />
                    </transition>
                    <button class="carousel-arrow right" @click="nextImage">›</button>
                </div>
                <div class="carousel-dots">
                    <span v-for="(image, index) in aicademiaImages" :key="index" :class="{ active: index === currentImageIndex }" class="dot" @click="setImageIndex(index)"></span>
                </div>
            </div>

            <div v-show="activeProject === 'WEATHER APP'" class="project-content">
                <p>
                    Aplikacja stworzona w języku Java (Swing) z wykorzystaniem API OpenWeatherMap informująca o pogodzie w wybranej
                    przez użytkownika lokalizacji.
                </p>
                <img :src="weatherAppImage.src" :alt="weatherAppImage.alt" class="project-image" />
            </div>
        </div>
    </transition>
</div>
</template>

    
<script>
export default {
    data() {
        return {
            activeProject: 'DOG BREED IDENTIFICATION',
            currentImageIndex: 0,
            dogBreedIdentificationImage: {
                src: '/images/projects/DBI/DBI.png',
                alt: 'Dog Breed Identification'
            },
            weatherAppImage: {
                src: '/images/projects/Weather/Weather.png',
                alt: 'Weather App'
            },
            estimationAppImages: [{
                    src: '/images/projects/EstimationApp/main.png',
                    alt: 'Main view'
                },
                {
                    src: '/images/projects/EstimationApp/clients.png',
                    alt: 'Clients view'
                },
                {
                    src: '/images/projects/EstimationApp/projects.png',
                    alt: 'Projects view'
                },
                {
                    src: '/images/projects/EstimationApp/estimations.png',
                    alt: 'Estimations view'
                },
                {
                    src: '/images/projects/EstimationApp/admin.png',
                    alt: 'Admin panel view'
                }
            ],
            aicademiaImages: [{
                    src: '/images/projects/Aicademia/game.png',
                    alt: 'Game view'
                },
                {
                    src: '/images/projects/Aicademia/difficulty.png',
                    alt: 'Difficulty view'
                },
                {
                    src: '/images/projects/Aicademia/conversation.png',
                    alt: 'Conversation view'
                },
                {
                    src: '/images/projects/Aicademia/boss.png',
                    alt: 'Boss view'
                }
            ]
        };
    },
    computed: {
        currentImage() {
            if (this.activeProject === 'ESTIMATION APP') {
                return this.estimationAppImages[this.currentImageIndex];
            } else if (this.activeProject === 'AICADEMIA') {
                return this.aicademiaImages[this.currentImageIndex];
            }
            return null;
        },
    },
    methods: {
        setActiveProject(project) {
            if (this.activeProject !== project) {
                this.activeProject = project;
                this.currentImageIndex = 0;
            }
        },
        prevImage() {
            if (this.activeProject === 'ESTIMATION APP') {
                this.currentImageIndex = (this.currentImageIndex - 1 + this.estimationAppImages.length) % this.estimationAppImages.length;
            } else if (this.activeProject === 'AICADEMIA') {
                this.currentImageIndex = (this.currentImageIndex - 1 + this.aicademiaImages.length) % this.aicademiaImages.length;
            }
        },
        nextImage() {
            if (this.activeProject === 'ESTIMATION APP') {
                this.currentImageIndex = (this.currentImageIndex + 1) % this.estimationAppImages.length;
            } else if (this.activeProject === 'AICADEMIA') {
                this.currentImageIndex = (this.currentImageIndex + 1) % this.aicademiaImages.length;
            }
        },
        setImageIndex(index) {
            this.currentImageIndex = index;
        }
    }
};
</script>

    
<style scoped>
.projects-section {
    padding: 20px;
    height: 80vh;
    text-align: center;
}

.projects-section h2 {
    margin-bottom: 20px;
    font-size: 24px;
    color: white;
}

.project-buttons {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 20px;
}

.project-button {
    background: none;
    border: none;
    color: white;
    font-size: 1em;
    padding: 10px;
    cursor: pointer;
    transition: color 0.3s ease;
}

.project-button:hover {
    color: #7060D3;
}

.project-button.active {
    color: #7060D3;
}

.project-details {
    text-align: center;
}

.project-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    color: white;
}

.project-content p {
    font-size: 1em;
    margin-bottom: 10px;
    max-width: 600px;
}

.project-image {
    margin-top: 15px;
    max-width: 100%;
    max-height: 250px;
    width: auto;
    height: auto;
    object-fit: contain;
    border-radius: 10px;
}

.carousel {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    margin-top: 5px;
    overflow: hidden;
    height: 250px;
}

.carousel-image {
    max-width: 100%;
    max-height: 250px;
    width: auto;
    height: auto;
    object-fit: contain;
    border-radius: 10px;
}

.carousel-arrow {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(0, 0, 0, 0.5);
    border: none;
    color: white;
    font-size: 2em;
    cursor: pointer;
    transition: background-color 0.3s ease;
    padding: 10px;
    border-radius: 10px;
}

.carousel-arrow.left {
    left: 10px;
}

.carousel-arrow.right {
    right: 10px;
}

.carousel-arrow:hover {
    background-color: #7060D3;
}

.carousel-dots {
    display: flex;
    justify-content: center;
    margin-top: 10px;
}

.dot {
    height: 10px;
    width: 10px;
    margin: 0 5px;
    background-color: #bbb;
    border-radius: 50%;
    display: inline-block;
    cursor: pointer;
}

.dot.active {
    background-color: #7060D3;
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.2s ease;
}

.fade-enter,
.fade-leave-to {
    opacity: 0;
}

.carousel-fade-enter-active,
.carousel-fade-leave-active {
    transition: opacity 0.2s ease;
}

.carousel-fade-enter,
.carousel-fade-leave-to {
    opacity: 0;
}
</style>