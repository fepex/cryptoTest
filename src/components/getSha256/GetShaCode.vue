<template>
    <div>
        <textarea v-model="textareaValue"></textarea>
        <button @click="sha256">Transform to SHA-256</button>
        <input disabled v-model="sha256Value">
    </div>
</template>

<script>
export default {
    name: 'GetShaCode',
    data() {
        return {
            textareaValue: '',
            sha256Value: '',
        }
    },
    methods: {
        async sha256() {
            const msgBuffer = new TextEncoder().encode(this.textareaValue);
            const hashBuffer = await crypto.subtle.digest('SHA-256', msgBuffer);
            const hashArray = Array.from(new Uint8Array(hashBuffer));
            const hashHex = hashArray.map(b => b.toString(16).padStart(2, '0')).join('');
            this.sha256Value = hashHex;
        }
    }
};
</script>