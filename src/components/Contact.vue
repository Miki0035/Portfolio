<template>
    <div id="contact" class="contact">
        <form ref="form" @submit="sendEmail" class="contact-container" v-if="!isLoading">
            <h2>Contact Me at any time </h2>
            <div class="form-element">
                <label for="name">Full Name</label>
                <input type="text" name="" id="name" v-model="fullName">
                <div class="errFullname errorMessage ">
                    Full name is required
                </div>
            </div>
            <div class="form-element">
                <label for="email">Email</label>
                <input type="email" id="email" placeholder="name@example.com" v-model="email">
                <div class="errEmail errorMessage">
                    Email is required
                </div>
            </div>
            <div class="form-element">
                <label for="text">Message:</label>
                <textarea name="" id="textarea" cols="20" rows="10" v-model="message"></textarea>
                <div class="errMessage errorMessage">
                    Message is required 
                </div>
            </div>
            <button>Send</button>
        </form>
        <div class="loading" v-show="isLoading">
            <h1> Loading...</h1>
        </div>
    </div>
</template>

<script>
import emailjs from '@emailjs/browser';
import { onMounted, ref } from 'vue';
import ScrollReveal from 'scrollreveal';
    export default {
        name: 'Contact',
        setup() {
            onMounted(() => {
                ScrollReveal().reveal('.contact', { delay: 100, origin: "bottom"})
            })
            
            let isLoading = ref(false);
            const form = ref(null);
            const fullName = ref("");
            const email = ref("");
            const message = ref("");
            const errorDivs = ref(["errFullname", "errEmail", "errMessage"]);
            
            async function sendEmail($event) {
                $event.preventDefault();
                let errors = [];
                if (fullName.value == "") {
                    errors.push("errFullname");
                }
                if (email.value == "") {
                    errors.push("errEmail");
                }
                if (message.value == "") {
                    errors.push("errMessage");
                }
                if (errors.length) {
                   for (let i = 0; i < errorDivs.value.length; i++) {
                        let errorDiv = document.querySelector(`.${errorDivs.value[i]}`);
                        for (let j = 0; j < errors.length; j++) {
                            if (errorDivs.value[i] == errors[j]) {
                                errorDiv.style.display = "block";
                                break;
                            } else {
                                errorDiv.style.display = "none";
                            }
                        }
                   }
                } else {
                    errorDivs.value.forEach(element => {
                        let errorDiv = document.querySelector(`.${element}`);
                        errorDiv.style.display = "none";
                    });
                    isLoading.value = true;
                    
                    var params = {
                        from_name: fullName.value,
                        email: email.value,
                        message: message.value,
                    }
                    try {
                        let resp = await emailjs.send("service_lk8h5x5", "template_kp4egj9", params, "FdvtoXWs-YNlo0Vi1");
                        alert('Message has been sent!');
                        isLoading.value = false;
                    } catch (err) {
                        console.log(err);
                        alert('Error has occured, Please try again');
                        isLoading.value = false;
                    }
                    
                    form.value.reset();
                    
                }                
            }

            return {
                fullName,
                email,
                message,
                isLoading,
                form,
                sendEmail,
            }
        }
    }
</script>
<style scoped>
.contact {
    width: 100%;   
    height: 100%;
    margin-top: 10%;
    display: flex;
    justify-content: center;
    align-items: center;    
}
.contact-container {
    background-color: var(--secondary-color);
    border-radius: 20%;
    padding: 30px 0;
    width: 70%;
    margin: 5% 0;
    display: flex;
    flex-direction: column;
    padding: 10px auto;
    align-items: center;
}
.contact-container h2 {
    text-align: center;
    font-size: 2.2rem;
    margin-bottom: 50px;
}
.form-element {
    width: 68%;
    display: flex;
    flex-direction: column;
}
.form-element label {
    font-size: 1.2rem;
    font-weight: 800;
    margin: 10px 0;
}
.form-element input, textarea {
    padding: 10px 15px;
    border-radius: 5px;
    background-color: var(--secondary-color);
    border: 1px solid var(--text-color);
    outline: none;
}
.contact-container button {
    margin: 20px 0;
    padding: 20px 4%;
    cursor: pointer;
    border-radius: 8px;
    background-color: var(--secondary-color);
    border: 2px solid var(--text-color);
    color: var(--text-color);
    transform: none;
    transition: all .2s ease-in-out;
}
.contact-container button:hover {
    border: 2px solid var(--secondary-color); 
    background-color: var(--secondary-color);
    color: var(--text-color);
    transform: scale(1.1);
    transition: all .2s ease-in-out;
}
.errorMessage {
    display: none;
    margin-top: 5px;
    color: #FF2511;
}
.loading {
    background-color: var(--secondary-color);
    padding: 30px 0;
    max-width: 70%;
    height: 100vh;
    margin: 5% 0;
    display: flex;
    justify-content: center;
}
.dark {
    --secondary-color: var(--dark-secondary-color);
    --text-color: var(--dark-text-color);
}

</style>