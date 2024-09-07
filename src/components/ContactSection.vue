<template>
<div class="contact-section">
    <p>SKONTAKTUJ SIĘ ZE MNĄ</p>
    <form @submit.prevent="sendEmail">
        <div class="data">
            <input v-model="name" class="name" type="text" placeholder="IMIĘ" required>
            <input v-model="lastName" class="last-name" type="text" placeholder="NAZWISKO" required>
            <input v-model="email" class="email" type="email" placeholder="E-MAIL" required>
        </div>
        <div class="message">
            <textarea v-model="message" class="message-textarea" placeholder="WIADOMOŚĆ..." required></textarea>
            <button class="send-button" type="submit">WYŚLIJ</button>
        </div>
    </form>
</div>
</template>

<script>
import {
    ref
} from 'vue';
import emailjs from 'emailjs-com';
import Swal from 'sweetalert2';
import {
    serviceID,
    templateID,
    userID
} from '../emailConfig';

export default {
    setup() {
        const name = ref('');
        const lastName = ref('');
        const email = ref('');
        const message = ref('');

        const sendEmail = async () => {
            try {
                const result = await emailjs.send(serviceID, templateID, {
                    from_name: `${name.value} ${lastName.value}`,
                    from_email: email.value,
                    message: message.value
                }, userID);

                console.log(result);
                Swal.fire({
                    icon: 'success',
                    title: 'Wiadomość została wysłana pomyślnie!',
                    background: '#222831',
                    color: '#d3d3d3',
                    didOpen: () => {
                        const swalPopup = Swal.getPopup();
                        swalPopup.style.borderRadius = '10px';
                    }
                });

                resetForm();
            } catch (error) {
                console.error(error);
                Swal.fire({
                    icon: 'error',
                    title: 'Wystąpił błąd',
                    text: 'Proszę spróbuj ponownie.',
                    background: '#222831',
                    color: '#d3d3d3',
                    didOpen: () => {
                        const swalPopup = Swal.getPopup();
                        swalPopup.style.borderRadius = '10px';
                    }
                });
            }
        };

        const resetForm = () => {
            name.value = '';
            lastName.value = '';
            email.value = '';
            message.value = '';
        };

        return {
            name,
            lastName,
            email,
            message,
            sendEmail
        };
    }
};
</script>

<style scoped>
.contact-section {
    padding: 20px;
    text-align: left;
}

.contact-section p {
    font-family: 'Roboto-Light', sans-serif;
    margin-bottom: 20px;
    font-size: 36px;
    color: white;
}

form {
    display: flex;
    gap: 20px;
    font-family: 'Roboto-Thin', sans-serif;
}

.data {
    position: relative;
    display: flex;
    flex-direction: column;
    gap: 15px;
}

.message {
    position: relative;
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: flex-end;
}

.name,
.last-name,
.email {
    background-color: #4a4a4a;
    color: #d3d3d3;
    border: none;
    padding: 10px;
    border-radius: 10px;
    transition: border-color 0.3s, color 0.3s;
}

.name:focus,
.last-name:focus,
.email:focus,
.message-textarea:focus {
    color: #ffffff;
    border: 2px solid #7060D3;
    outline: none;
}

.message-textarea {
    background-color: #4a4a4a;
    color: #d3d3d3;
    width: 100%;
    height: 15vh;
    border: none;
    padding: 10px;
    border-radius: 10px;
    box-sizing: border-box;
    resize: none;
    transition: border-color 0.3s, color 0.3s;
}

.send-button {
    display: inline-flex;
    color: white;
    margin-top: 15px;
    color: #ffffff;
    text-decoration: none;
    border: 2px solid #ffffff;
    padding: 0.5rem 1rem;
    border-radius: 10px;
    transition: background-color 0.3s ease, color 0.3s ease;
}

.send-button:hover {
    background-color: #7060D3;
    color: #ffffff;
}

@media (max-width: 768px) {
    form {
        flex-direction: column;
        gap: 20px;
    }

    .message {
        width: 100%;
    }

    .data {
        width: 100%;
    }
}
</style>