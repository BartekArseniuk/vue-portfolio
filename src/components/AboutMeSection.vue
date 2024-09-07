<template>
<div class="about-me-section">
    <div class="text-container">
        <p class="title">O MNIE</p>
        <p class="description">Cześć! Jestem początkującym programistą. Moja pasja skupia się na tworzeniu projektów front-endowych. Na codzień pracuję nad rozwijaniem własnych projektów, zarówno webowych, jak i mobilnych. Chociaż głównie zajmuję się warstwą użytkownika, mam również podstawową wiedzę z zakresu back-endu, co pozwala mi lepiej rozumieć pełny cykl tworzenia aplikacji.</p>
    </div>
</div>
</template>

<style scoped>
.about-me-section {
    background-image: url('/public/images/other/about_me.png');
    background-size: cover;
    background-position: center;
    height: auto;
    display: flex;
    justify-content: right;
    z-index: 98;
    position: relative;
}

.text-container {
    padding: 40px 40px;
    text-align: right;
    width: 70%;
}

.title {
    font-size: 50px;
    margin-bottom: 20px;
    font-family: 'Roboto-Light', sans-serif;
}

.description {
    font-size: 26px;
    word-wrap: break-word;
    font-family: 'Roboto-Extra-Light', sans-serif;
}

@media (max-width: 768px) {
    .text-container {
        width: 100%;
    }
}
</style>