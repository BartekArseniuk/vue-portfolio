<template>
<div class="contact-section">
    <h2>CONTACT ME</h2>
    <form>
        <div class="data">
            <input class="name" type="text" placeholder="NAME" required>
            <input class="last-name" type="text" placeholder="LAST NAME" required>
            <input class="email" type="email" placeholder="E-MAIL" required>
        </div>
        <div class="message">
            <textarea class="message-textarea" placeholder="YOUR MESSAGE..." required></textarea>
            <button class="send-button" type="submit">SEND</button>
        </div>
    </form>
</div>
</template>

<style scoped>
.contact-section {
    padding: 20px;
    text-align: left;
}

.contact-section h2 {
    margin-bottom: 20px;
    font-size: 36px;
    color: white;
}

form {
    display: flex;
    gap: 20px;
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
    background-color: #343B45;
    color: #6E6E6E;
    border: none;
    padding: 10px;
    border-radius: 4px;
}

.message-textarea {
    background-color: #343B45;
    color: #6E6E6E;
    width: 100%;
    height: 15vh;
    border: none;
    padding: 10px;
    border-radius: 4px;
    box-sizing: border-box;
    resize: none;
}

.send-button {
    background-color: #7060D3;
    color: white;
    margin-top: 15px;
    border: none;
    padding: 10px 20px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 16px;
    transition: background-color 0.5s ease;
}

.send-button:hover {
    background-color: #6351d6;
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