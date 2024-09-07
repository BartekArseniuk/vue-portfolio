<template>
<div class="home-section">
    <div class="profile">
        <h1 class="name">Bartosz Arsenik</h1>
        <p class="description">Początkujący programista, student informatyki na Akademii Bialskiej im. Jana Pawła II.</p>
        <div class="social-links">
            <a href="https://github.com/BartekArseniuk" target="_blank" class="social-link" aria-label="GitHub">
                <v-icon class="social-icon">mdi-github</v-icon>
            </a>
            <a href="https://www.facebook.com/bartek.arseniuk.9/" target="_blank" class="social-link" aria-label="Facebook">
                <v-icon class="social-icon">mdi-facebook</v-icon>
            </a>
        </div>
        <a href="#" class="get-started" @click="scrollDown">Zaczynajmy <v-icon class="arrow-icon">mdi-chevron-right</v-icon></a>
    </div>
    <div class="images-container">
        <img src="/images/other/me.png" alt="Profile Avatar" class="avatar-img">
    </div>
</div>
</template>

<script>
export default {
    methods: {
        scrollDown(event) {
            event.preventDefault();
            window.scrollBy({
                top: window.innerHeight * 0.8,
                behavior: 'smooth'
            });
        }
    }
}
</script>

<style scoped>
.home-section {
    position: relative;
    height: 100vh;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    overflow: hidden;
    background: linear-gradient(to right, #1c1c1c, #3a3a3a);
}

.profile {
    position: absolute;
    top: 50%;
    left: 5%;
    transform: translateY(-50%);
    color: #ffffff;
    text-align: left;
    z-index: 4;
}

.name {
    font-size: 4rem;
    font-family: 'Roboto-Light', sans-serif;
    margin: 0;
    line-height: 1.2;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}

.description {
    font-size: 1.6rem;
    font-family: 'Roboto-Extra-Light', sans-serif;
    max-width: 500px;
    margin-top: 0.5rem;
    line-height: 1.5;
    text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3);
}

.social-links {
    margin-top: 1rem;
    display: flex;
    align-items: center;
    z-index: 4;
}

.social-link {
    margin-right: 0.8rem;
}

.social-icon {
    font-size: 3rem;
    color: #ffffff;
    transition: color 0.3s ease;
}

.social-icon:hover {
    color: #7060D3;
}

.get-started {
    display: inline-flex;
    align-items: center;
    margin-top: 1.5rem;
    font-size: 1.2rem;
    font-family: 'Roboto-Light', sans-serif;
    color: #ffffff;
    text-decoration: none;
    border: 2px solid #ffffff;
    padding: 0.5rem 1rem;
    border-radius: 0.5rem;
    transition: background-color 0.3s ease, color 0.3s ease;
}

.get-started:hover {
    background-color: #7060D3;
    color: #ffffff;
}

.arrow-icon {
    margin-left: 0.5rem;
    font-size: 1.5rem;
}

.images-container {
    position: absolute;
    top: 0;
    right: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    z-index: 1;
}

.avatar-img {
    position: absolute;
    bottom: 10%;
    right: 5%;
    width: 40vw;
    height: auto;
    border-radius: 50%;
    z-index: 3;
}

@media (max-width: 768px) {
    .profile {
        left: auto;
        right: 20px;
        text-align: right;
        width: 90%;
        transform: none;
        top: 15%;
    }

    .name {
        font-size: 2.8rem;
    }

    .description {
        font-size: 1.4rem;
        max-width: none;
        text-align: right;
    }

    .social-links {
        justify-content: flex-end;
        width: auto;
        margin-top: 1rem;
    }

    .social-link {
        margin-right: 1.2rem;
    }

    .social-icon {
        font-size: 3.5rem;
    }

    .avatar-img {
        width: 90vw;
        bottom: 5%;
        left: 5%;
    }

    .get-started {
        margin-top: 1.5rem;
        align-self: flex-end;
        font-size: 1.5rem;
    }
}
</style>