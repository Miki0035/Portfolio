<template>
    <div class="app-navbar-container">
        <div class="app-navbar-links">
            <ul>
                <li><a href="#home">About Me</a></li>
                <li><a href="#projects">Projects</a></li>
                <li><a href="#contact">Contact Me</a></li>
                <li><a @click="toDarkMode"><box-icon id="boxIcon" type='solid' name='moon' :color="fontColor"></box-icon></a>
                </li>
            </ul>
        </div>
        <div class="hidden-app-navbar">
            <div class="hamburger-icon" @click="showMenu">
                <div class="bar"></div>
                <div class="bar"></div>
                <div class="bar"></div>
            </div>
            <div class="hidden-app-links">
                <ul>
                    <li><a href="#home">Home</a></li>
                    <li><a href="#projects">Projects</a></li>
                    <li><a href="#contact">Contact Me</a></li>
                </ul>
            </div>
            <a @click="toDarkMode"><box-icon id="boxIcon" type='solid' name='moon' :color="fontColor"></box-icon></a>
        </div>
        <div>

        </div>
    </div>
    <h3>Welcome , To Me</h3>
</template>

<script>
import Scrollreveal from 'scrollreveal';
import { ref, onMounted, provide } from 'vue';
    export default {
        name: 'Navbar',
        setup() {
            let darkMode = ref(false);
            let fontColor = ref("black");
            onMounted(() => {
                Scrollreveal().reveal("h3", { delay: 100, origin:"top"});
            });
            provide("darkMode", darkMode);

            function toDarkMode() {
                let dark = ref(document.getElementById("boxIcon"));
                let app = document.querySelector("#main-div");
                let profile = document.querySelector("#home");
                let projects = document.querySelector("#projects");
                let contact = document.querySelector("#contact");


                if (dark.value.attributes.name.value === "moon") {
                    dark.value.attributes.name.value = "sun";
                    dark.value.attributes.type.value = "solid";
                    darkMode.value = true;
                    fontColor.value = "white";
                    app.classList.add("dark");
                    profile.classList.add("dark");
                    projects.classList.add("dark");
                    contact.classList.add("dark");
                } else {
                    dark.value.attributes.name.value = "moon";
                    dark.value.attributes.type.value = "solid";
                    darkMode.value = false;
                    fontColor.value = "black";
                    app.classList.remove("dark");
                    profile.classList.remove("dark");
                    projects.classList.remove("dark");
                    contact.classList.remove("dark");

                }
            };
            function showMenu() {
                let menuIcon = document.querySelector('.hamburger-icon');
                let menuLinks = document.querySelector('.hidden-app-links');
                menuIcon.classList.toggle("close");
                menuLinks.classList.toggle("show");
            }
            return {
                toDarkMode,
                showMenu,
                darkMode,
                fontColor
            }
        }
    }   
</script>

<style scoped>
h3 {
    text-align: center;
    font-size: 5.5rem;
    margin-bottom: 20%;
    padding: 40px 5%;
}
.app-navbar-container {
    display: flex;
    position: relative;
    padding: 20px 5%;
    max-width: 100%;
    justify-content: center;
    align-items: center;
}
.app-navbar-links {
    margin: 5% 30px;
    padding: 10px 20px;
    max-width: 1200px;
    min-height: 2em;
}
.app-navbar-links ul {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    font-size: 1.5rem;
}
.app-navbar-links ul li {
    list-style: none;
    margin: 0 20px;
}
.app-navbar-links ul li a {
    text-decoration: none;
    cursor: pointer;
}
.app-navbar-links a:hover {
    color: #fff;
}
.hidden-app-navbar {
    display: none;
    position: relative;
    width: 100%;
    justify-content: space-between;
    align-items: center;
}
.hidden-app-navbar a {
    margin-right: 20px;
}
.hamburger-icon > div {
    display: block;
    margin: 0 10%;
    width: 40px;
    height: 5px;
    margin: 6px 15%;
    background-color: var(--text-color);
    transform: none;
    transition: transform .3s ease-in-out;
}
.hamburger-icon.close .bar:first-child {
    transform: translateY(6px) rotate(45deg);
}
.hamburger-icon.close .bar:nth-child(2) {
    opacity: 0;
}
.hamburger-icon.close .bar:last-child {
    transform: translateY(-6px) rotate(-45deg);
}
.hidden-app-links {
    display: none;
    position: absolute;
    top: 0;
    left: 40%;
}
.hidden-app-links.show {
    display: block;
}
.hidden-app-links ul {
    list-style-type: none;
}
.hidden-app-links ul li a {
    text-decoration: none;
    color: var(--text-color);
}

@media (max-width: 790px) {
    .hidden-app-navbar {
        display: flex;
    }
    .app-navbar-links {
        display: none;
    }
    h3 {
        width:  100%;
        margin: 0 auto;
        font-size: 2rem;
    }
}
</style>