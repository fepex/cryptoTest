<template>
    <div>
        <textarea v-model="textareaValue"
            :placeholder="'Напишите фразу которую хотите ' + textareaPlaceholder"></textarea>
        <input v-model="secret" placeholder="секретная фраза">
        <div v-if="encrypted">
            <button @click="aesEncrypt">Зашифровать</button>
            <input disabled v-model="encryptedValue">
        </div>
        <div v-else>
            <button @click="aesDecrypt">Расшифровать</button>
            <input disabled v-model="decryptedValue">
        </div>
    </div>
</template>

<script>
import CryptoJS from 'crypto-js';

export default {
    name: 'GetShaCode',
    props: {
        encrypted: Boolean,
    },
    data() {
        return {
            textareaValue: '',
            textareaPlaceholder: this.encrypted ? 'зашифровать' : 'дешифровать',
            secret: '',
            encryptedValue: '',
            decryptedValue: '',
        }
    },
    methods: {
        async aesEncrypt() {
            this.encryptedValue = CryptoJS.AES.encrypt(this.textareaValue, this.secret).toString();
        },
        async aesDecrypt() {
            this.decryptedValue = CryptoJS.AES.decrypt(this.textareaValue, this.secret).toString(CryptoJS.enc.Utf8)
        }
    }
};
</script>

<style scoped>
textarea,
input,
button {
    margin-right: 10px;
}
</style>