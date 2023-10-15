<template>
    <div id="projects" class="projects">
        <h1>My Projects</h1>
        <div class="project-cards-container" >
            <div class="project-card" v-for="item in items" :key="item.title">
                <div class="project-card-img">
                    <img :src="item.imageFrame" alt="Frame work image">    
                    <img :src="item.imagePro" alt="Frame work image">
                </div>
                <div class="project-card-content">
                    <h4>{{ item.title }}</h4>
                    <p>
                        {{ item.desc }}
                    </p>
                </div>
                <a :href="item.link">Go to Project</a>
            </div>
        </div>
    </div>
</template>

<script>
import { ref, onMounted } from 'vue';
import ScrollReveal from 'scrollreveal';
import { projects } from "../project.js";
    export default {
        name: 'Projects',
        setup() {
            const items = ref(projects);
            onMounted(() => {
                ScrollReveal().reveal(".project-cards-container", { delay:100, origin: "left"});
            })
            return {
                items
            }
        }
    }
</script>

<style scoped>
.projects {
    margin: 10% auto;
    width: 100%;
    padding: 20px 3%;
}
h1 {
    font-size: 4.5rem;
}
.project-cards-container {
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    margin: 5% auto;
    max-width: 100%;
    min-height: 100%;
}
.project-card {
    display: flex;
    max-width: 20%;
    min-height: 450px;
    background-color: var(--secondary-color);
    flex-direction: column;
    padding: 30px 20px; 
    transform: none;
    transition: all .33s ease-in-out;
    cursor: pointer;
    border-radius: 10px;
}
.project-card-img {
    display: flex;
    justify-content: space-around;
    align-items: center;
}
.project-card img {
    width: 50%;
}
.project-card-content {
    display: flex;
    margin-top: 15%;
    flex-direction: column;
} 
.project-card-content h4 {
    text-align: left;
    font-size: 1.2rem;
    margin-bottom: 20px;
}
.project-card-content p {
    font-size: 1rem;
    text-align: left;
    padding: 10px 5px;
}
.project-card a {
    align-self: center;
    text-align: center;
    text-decoration: none;
    padding: 10px 5px;
    border: 1px solid var(--text-color);
    width: 50%;
    margin: 5px;
    border-radius: 5px;
}
.project-card a:hover {
    color: var(--secondary-color);
    background-color: var(--text-color);
}
div.project-card:hover {
    transform: translate3d(-10px, -20px, -30px);
    transition: all .33s ease-in-out;
}
.dark {
    --secondary-color: var(--dark-secondary-color);
    --text-color: var(--dark-text-color);
}
</style>