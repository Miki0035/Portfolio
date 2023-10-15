<template>
    <div id="home" class="app-profile-container">
        <div class="app-profile-card">
            <img src="../assets/MIKIYAS_KEBEDE_600x600 px.jpg" alt="profile image">
            <div class="app-profile-card-socials">
                <a href="#">
                    <box-icon size="50px"  name='twitter' type='logo' color="var(--text-color)" ></box-icon>
                </a>
                <a href="#">
                    <box-icon size="50px" type='logo' name='linkedin-square' color="var(--text-color)"></box-icon> 
                </a>  
                <a href="#">
                    <box-icon size="50px" name='github' type='logo' color="var(--text-color)"></box-icon>
                </a>
                <a href="#">
                    <box-icon size="50px" name='facebook-circle' type='logo' color="var(--text-color)" ></box-icon>
                </a>
                <a href="#">
                    <box-icon size="50px" name='telegram' type='logo' color="var(--text-color)" ></box-icon>
                </a>
            </div>
        </div>
        <div class="app-profile-about">
            <p>
                Greetings and Welcome , I am a talented full stack developer always striving to be 
                better at my job. Being fluent in multiple programming languages and familiar
                with popular frameworks , I know I am the right fit for the job. Please checkout
                my projects and tell me what you think 
            </p>
        </div>
    </div>
</template>

<script>
import 'boxicons'
import { onMounted } from 'vue';
import ScrollReveal from 'scrollreveal';
    export default {
        name: 'Profile',
        setup() {
            const slide = ScrollReveal({
                distance: '70px',
                duration: 2700,
                reset: true,
            });
            onMounted(() => {
                ScrollReveal().reveal(".app-profile-container", { delay:100, origin: "left"});
                ScrollReveal().reveal(".app-profile-about", { delay:100, origin: "right"});

            })
        }
    }
</script>   

<style scoped>

.app-profile-container {
    max-width: 80%;
    margin: 0 auto;
    min-height: 50%;
    background-color: var(--secondary-color);
    display: flex;
    padding: 50px 5%;
    border-radius: 20%;
    justify-content: space-evenly;
}
.app-profile-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 2% 40px;
    padding: 40px 30px;
    transform: none;
    transition: all .3s;
}
div.app-profile-card:hover {
    transform: scale(1.1);
    transition: all .3s;
} 
.app-profile-card img {
    width:  100%;
    border-radius: 50%;
    margin: 30px 5px;
}
.app-profile-card-socials {
    display: flex;
    justify-content: space-evenly;
    margin-top: 35px;
}
.app-profile-card-socials a box-icon {
    margin: 0 10px;
    max-width: 50%;
    border-radius: 50%;
    transition: all .3s;
    color: var(--main-color);
}
.app-profile-card-socials a:hover {
    transform: scale(1.2);
    transition: all .3s;
}

.app-profile-about {
    display: flex;
    align-items: center;
    font-size: 1.5rem;
    line-height: 2.1rem;

}
.dark {
    --secondary-color: var(--dark-secondary-color);
    --main-color: var(--dark-text-color);
    --text-color: var(--dark-text-color);
}
</style>