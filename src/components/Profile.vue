<template>
    <div id="home" class="app-profile-container">
        <div class="app-profile-card">
            <img src="../assets/MIKIYAS_KEBEDE_600x600 px.jpg" alt="profile image">
            <div class="app-profile-card-socials">
                <a href="https://twitter.com/@Mikiyas76212789" target="_blank">
                    <box-icon size="var(--size)"  name='twitter' type='logo' color="var(--text-color)" ></box-icon>
                </a>
                <a href="https://www.linkedin.com/in/mikiyas-kebede-b661aa225" target="_blank" >
                    <box-icon size="var(--size)" type='logo' name='linkedin-square' color="var(--text-color)"></box-icon> 
                </a>  
                <a href="https://github.com/Miki0035" target="_blank">
                    <box-icon size="var(--size)" name='github' type='logo' color="var(--text-color)"></box-icon>
                </a>
                <a href="https://www.facebook.com/mikiyas.kebede.3950" target="_blank">
                    <box-icon size="var(--size)" name='facebook-circle' type='logo' color="var(--text-color)" ></box-icon>
                </a>
                <a href="https://t.me/helloworldman123" target="_blank">
                    <box-icon size="var(--size)" name='telegram' type='logo' color="var(--text-color)" ></box-icon>
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
.app-profile-card-socials a {
    margin: 0 10px;
    --size: 50px;
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
@media (max-width: 1200px) {
    .app-profile-container{
        display: flex;
        flex-direction: column;
    }
    .app-profile-card img {
        width: 50%;
    }
    .app-profile-card-socials a {
        margin: 0 15px;
        width: 40px;
        height: 40px;
        text-align: center;
        --size: 50px;
    }
    .app-profile-about {
        margin: 0;
        line-height: 25px;
    }
    .app-profile-about p {
        font-size: 1.2rem;   
        margin: 0;
        width: 100%;
        margin: 0 auto;
    }

}
@media (max-width: 900px) {
    .app-profile-card-socials a {
        margin: 0 10px;
        --size: 40px;
    }
    .app-profile-about p {
        margin: 0 auto;
        text-align: center;
        font-size: 1.1rem;
    }
}
@media (max-width: 790px) {
    .app-profile-card img {
        width: 200px;
    }
    .app-profile-card-socials a {
        margin: 0 10px;
        --size: 35px;
    }
    .app-profile-about p {
        font-size: 1rem;
        text-align: center;
    }
}
</style>