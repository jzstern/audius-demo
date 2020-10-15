<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,<br />
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener"
        >vue-cli documentation</a
      >.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li>
        <a
          href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel"
          target="_blank"
          rel="noopener"
          >babel</a
        >
      </li>
      <li>
        <a
          href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint"
          target="_blank"
          rel="noopener"
          >eslint</a
        >
      </li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li>
        <a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a>
      </li>
      <li>
        <a href="https://forum.vuejs.org" target="_blank" rel="noopener"
          >Forum</a
        >
      </li>
      <li>
        <a href="https://chat.vuejs.org" target="_blank" rel="noopener"
          >Community Chat</a
        >
      </li>
      <li>
        <a href="https://twitter.com/vuejs" target="_blank" rel="noopener"
          >Twitter</a
        >
      </li>
      <li>
        <a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a>
      </li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li>
        <a href="https://router.vuejs.org" target="_blank" rel="noopener"
          >vue-router</a
        >
      </li>
      <li>
        <a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a>
      </li>
      <li>
        <a
          href="https://github.com/vuejs/vue-devtools#vue-devtools"
          target="_blank"
          rel="noopener"
          >vue-devtools</a
        >
      </li>
      <li>
        <a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener"
          >vue-loader</a
        >
      </li>
      <li>
        <a
          href="https://github.com/vuejs/awesome-vue"
          target="_blank"
          rel="noopener"
          >awesome-vue</a
        >
      </li>
    </ul>
  </div>
</template>

<script>
/* eslint-disable */
import Audius from "@audius/libs"

export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  async mounted() {
    var init = async () => {
    const dataRegistryAddress = '0xC611C82150b56E6e4Ec5973AcAbA8835Dd0d75A2'

    const ethTokenAddress = '0xADEf65C0f6a30Dcb5f88Eb8653BBFe09Bf99864f'
    const ethRegistryAddress = '0xb2be26Ca062c5D74964921B80DE6cfa28D9A36c0'
    const ethProviderUrl = 'https://mainnet.infura.io/v3/d6b566d7eea1408988388c311d5a273a'
    const ethProviderOwnerWallet = '0xe886a1858d2d368ef8f02c65bdd470396a1ab188'

    const libs = new Audius({
      web3Config: Audius.configInternalWeb3(
        dataRegistryAddress,
        ['https://core.poa.network']
      ),
      ethWeb3Config: Audius.configEthWeb3(
        ethTokenAddress,
        ethRegistryAddress,
        ethProviderUrl,
        ethProviderOwnerWallet
      ),
      discoveryProviderConfig: Audius.configDiscoveryProvider(),
      identityServiceConfig: Audius.configIdentityService(
        'https://identityservice.audius.co'
      ),
      creatorNodeConfig: Audius.configCreatorNode(
        'https://creatornode.audius.co'
      )
    })
    await libs.init()
    window.libs = libs
    return libs
  }

    const libs = await init()
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
