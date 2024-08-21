<template>
    <div>
        <div v-if="!isLoggedIn">
            <button @click="connectWallet" v-if="isMetamaskSupported">Metamask Login</button>
            <h3 v-else>Install Metamask extension</h3>
        </div>

        <div v-else>
            {{ address }}
        </div>
    </div>
</template>

<script>
import Web3 from 'web3';

export default {
    name: 'MetamaskWallet',
    data() {
        return {
            isLoggedIn: false,
            address: "",
            isMetamaskSupported: false,
        }
    },
    mounted() {
        this.isMetamaskSupported = typeof window.ethereum !== 'undefined';
    },
    methods: {
        async getWeb3() {
            return new Promise((resolve, reject) => {
                const web3 = new Web3(window.ethereum);
                try {
                    window.ethereum.request({ method: "eth_requestAccounts" });
                    resolve(web3);
                } catch (error) {
                    reject(error);
                }
            })
        },
        async connectWallet() {
            const web3 = await this.getWeb3();
            const walletsAddresses = await web3.eth.requestAccounts();
            console.log(walletsAddresses);
            if (walletsAddresses) {
                this.address = walletsAddresses[0];
                this.isLoggedIn = true;
            }
        }
    }
};
</script>