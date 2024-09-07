<template>
<div class="home-section">
    <div class="profile">
        <p class="name">BARTOSZ ARSENIUK</p>
        <p class="description">Początkujący programista, student informatyki na Akademii Bialskiej im. Jana Pawła II.</p>
        <div class="social-links">
            <a href="https://github.com/BartekArseniuk" target="_blank" class="social-link">
                <v-icon class="social-icon">mdi-github</v-icon>
            </a>
            <a href="https://www.facebook.com/bartek.arseniuk.9/" target="_blank" class="social-link">
                <v-icon class="social-icon">mdi-facebook</v-icon>
            </a>
        </div>
    </div>
    <div class="images-container">
        <img src="/images/other/dashed.png" alt="dashed" class="dashed-img">
        <img src="/images/other/circle.png" alt="circle" class="circle-img">
        <img src="/images/other/me.png" alt="avatar" class="avatar-img">
    </div>
</div>
</template>

<style scoped>
.home-section {
    position: relative;
    height: 100vh;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    overflow: hidden;
}

.profile {
    position: absolute;
    top: 100px;
    left: 30px;
    color: white;
    text-align: left;
    z-index: 4;
}

.name {
    font-size: 3rem;
    font-family: 'Roboto-Light', sans-serif;
    margin: 0;
}

.description {
    font-size: 1.5rem;
    font-family: 'Roboto-Extra-Light', sans-serif;
    width: 80%;
    max-width: 600px;
    margin-top: 0.5rem;
    text-align: left;
}

.social-links {
    margin-top: 0.5rem;
    display: flex;
    align-items: center;
    z-index: 4;
    padding: 0.5rem;
    border-radius: 0.5rem;
    background-color: #222831;
}

.social-link {
    margin-right: 0.5rem;
}

.social-icon {
    font-size: 2.5rem;
    color: white;
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

.dashed-img {
    position: absolute;
    top: 50%;
    width: 20%;
    height: auto;
    z-index: 2;
}

.circle-img {
    position: absolute;
    top: 75%;
    left: 10%;
    width: 20%;
    height: auto;
    z-index: 2;
}

.avatar-img {
    position: absolute;
    bottom: 0;
    right: 5%;
    width: 50vw;
    height: 80vh;
    z-index: 3;
}

@media (max-width: 768px) {
    .profile {
        left: auto;
        right: 20px;
        text-align: right;
        width: 80%;
    }

    .name {
        font-size: 2.5rem;
    }

    .description {
        font-size: 1.5rem;
        width: 100%;
        max-width: none;
        text-align: right;
    }

    .social-links {
        justify-content: flex-end;
        width: auto;
        margin-top: 1rem;
    }

    .social-link {
        margin-right: 1rem;
    }

    .social-icon {
        font-size: 3rem;
    }

    .avatar-img {
        height: auto;
        width: 100%;
    }

    .dashed-img {
        width: 50%;
        top: 60%;
    }

    .circle-img {
        width: 50%;
        top: 45%;
        left: -20%;
    }
}
</style>