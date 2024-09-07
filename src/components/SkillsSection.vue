<template>
<div class="skills-section">
    <p>UMIEJĘTNOŚCI</p>
    <ul class="skills-list">
        <li v-for="(skill, index) in skills" :key="index" class="skill">
            {{ skill }}
        </li>
    </ul>
</div>
</template>

<script>
export default {
    name: 'SkillsSection',
    data() {
        return {
            skills: [
                'JAVA, SWING',
                'ANDROID (JAVA), MVVM, ROOM',
                'REST API',
                'MySQL',
                'PODSTAWY C#',
                'HTML, CSS, JAVASCRIPT, BOOTSTRAP',
                'PODSTAWY NODEJS',
                'PODSTAWY REACTJS, VUEJS',
                'PODSTAWY PHP, LARAVEL',
                'SCRUM',
                'KANBAN',
                'GIT'
            ]
        };
    }
};
</script>

<style scoped>
.skills-section {
    background: linear-gradient(to right, #1c1c1c, #3a3a3a);
    color: #ffffff;
    padding: 20px;
    text-align: center;
    box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
}

.skills-section p {
    margin-bottom: 20px;
    font-size: 24px;
    font-family: 'Roboto-Light', sans-serif;
    letter-spacing: 2px;
}

.skills-list {
    padding-left: 0;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    font-family: 'Roboto-Thin', sans-serif;
}

.skills-list li::marker {
    font-size: 26px;
    color: #7060D3;
}

.skill {
    margin: 5px 10px;
    font-size: 18px;
    color: white;
    list-style-position: inside;
}
</style>