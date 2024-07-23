<template>
<div class="home-section">
    <div class="profile">
        <h2>Bartosz Arseniuk</h2>
        <p>Początkujący programista, student trzeciego roku informatyki na Akademii Bialskiej im. Jana Pawła II.</p>
    </div>
</div>
<div class="images-container">
    <img src="/images/other/dashed.png/" alt="dashed" class="dashed-img">
    <img src="/images/other/circle.png/" alt="circle" class="circle-img">
    <img src="/images/other/me.png" alt="avatar" class="avatar-img">
</div>
</template>

<style scoped>
.home-section {
    position: relative;
    height: 100vh;
    z-index: 1;
}

.profile {
    position: absolute;
    top: 100px;
    left: 30px;
    color: white;
    text-align: left;
}

.home-section h2 {
    font-size: 40px;
}

.home-section p {
    font-size: 24px;
    width: 50%;
}

.images-container {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}

.dashed-img {
    position: absolute;
    top: 60%;
    left: 0;
    z-index: 1;
}

.circle-img {
    position: absolute;
    top: 75%;
    left: 10%;
    z-index: 1;
}

.avatar-img {
    position: absolute;
    bottom: 0;
    right: 10%;
    max-width: 100vw;
    max-height: 400px;
    z-index: 1;
}
</style>