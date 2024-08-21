<template>
  <ol>
    <li>
      <MetamaskWallet />
    </li>
    <li>
      <GetShaCode />
    </li>
    <li>
      <DockPanel />
    </li>
    <li>
      <AesEncryption :encrypted="true" />
    </li>
    <li>
      <AesEncryption :encrypted="false" />
    </li>
  </ol>
</template>

<script>
import MetamaskWallet from './components/metamask/MetamaskWallet.vue';
import GetShaCode from './components/getSha256/GetShaCode.vue';
import DockPanel from './components/dockPanel/DockPanel.vue';
import AesEncryption from './components/aesEncryption/AesEncryption.vue';

export default {
  name: 'App',
  components: {
    MetamaskWallet,
    GetShaCode,
    DockPanel,
    AesEncryption
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

ol {
  font-size: 1.5rem;
}

li {
  line-height: 1.5;
  padding-top: 20px;
}
</style>
