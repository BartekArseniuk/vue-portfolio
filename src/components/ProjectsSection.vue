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
                    Aplikacja webowa pozwalająca na zarządzanie projektami klientów oraz ich wycenami. Back-end stworzoy na Laravel'u, natomiast Front-end wykorzystuje VueJS oraz Vuetify Material Design.
                </p>
                <div class="carousel">
                    <button class="carousel-arrow left" @click="prevImage">‹</button>
                    <img :src="currentImage.src" :alt="currentImage.alt" class="carousel-image" />
                    <button class="carousel-arrow right" @click="nextImage">›</button>
                </div>
            </div>

            <div v-show="activeProject === 'AICADEMIA'" class="project-content">
                <p>
                    Webowa gra edukacyjna skierowana do najmłodszych i nie tylko. Pozwala ona uczyć się nowych słów z języka angielskiego. Dobór poziomu słownictwa wybiera sam użytkownik — od A1 do C2. Każdego dnia losowane są nowe słowa oraz role postaci, które spotykamy na wyspie. Po rozmowach z mieszkańcami wyspy użytkownik może sprawdzić swoją wiedzę w walce z bossem w formie testu.
                </p>
                <div class="carousel">
                    <button class="carousel-arrow left" @click="prevImage">‹</button>
                    <img :src="currentAICademiaImage.src" :alt="currentAICademiaImage.alt" class="carousel-image" />
                    <button class="carousel-arrow right" @click="nextImage">›</button>
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
            currentAICademiaIndex: 0,
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
            return this.estimationAppImages[this.currentImageIndex];
        },
        currentAICademiaImage() {
            return this.aicademiaImages[this.currentAICademiaIndex];
        }
    },
    methods: {
        setActiveProject(project) {
            requestAnimationFrame(() => {
                if (this.activeProject !== project) {
                    this.activeProject = project;
                    this.currentImageIndex = 0;
                    this.currentAICademiaIndex = 0;
                }
            });
        },
        prevImage() {
            if (this.activeProject === 'ESTIMATION APP') {
                this.currentImageIndex = (this.currentImageIndex - 1 + this.estimationAppImages.length) % this.estimationAppImages.length;
            } else if (this.activeProject === 'AICADEMIA') {
                this.currentAICademiaIndex = (this.currentAICademiaIndex - 1 + this.aicademiaImages.length) % this.aicademiaImages.length;
            }
        },
        nextImage() {
            if (this.activeProject === 'ESTIMATION APP') {
                this.currentImageIndex = (this.currentImageIndex + 1) % this.estimationAppImages.length;
            } else if (this.activeProject === 'AICADEMIA') {
                this.currentAICademiaIndex = (this.currentAICademiaIndex + 1) % this.aicademiaImages.length;
            }
        }
    }
};
</script>

<style scoped>
.projects-section {
    padding: 20px;
    height: auto;
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
    margin-top: 15px;
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

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.5s ease;
}

.fade-enter,
.fade-leave-to {
    opacity: 0;
}
</style>