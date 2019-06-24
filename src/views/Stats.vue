<template lang="pug">
div.container
  h1 Thankful Stats
  div
    label(for="creator")
      | Show stats for creator:
    div(style="display: flex")
      input#creator(placeholder="Enter an email, profile, or Ethereum address", style="flex-grow: 3", v-model="creator_id")
      button.btn.btn-primary(@click="lookup", style="flex-grow: 1") Go!

  div
    h2(style="margin-bottom: 0") Top creators
    sub Creators of the free internet
    ol
      li
        | Metamask (GitHub)
      li
        | DataDash (YT)

    div
      h2(style="margin-bottom: 0") Top supporters
      sub Heroes of the free internet
      ol
        li
          | @ErikBjare
        li
          | 0x12312312312313
</template>

<script>
import Vue from "vue";
import BootstrapVue from "bootstrap-vue";

import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";
Vue.use(BootstrapVue);

import Web3 from "web3";

window.addEventListener("load", async () => {
  // Modern dapp browsers...
  if (window.ethereum) {
    window.web3 = new Web3(ethereum);
    try {
      // Request account access if needed
      await ethereum.enable();
      // Accounts now exposed
      //web3.eth.sendTransaction({/* ... */});
    } catch (error) {
      // User denied account access...
    }
  }
  // Legacy dapp browsers...
  else if (window.web3) {
    window.web3 = new Web3(web3.currentProvider);
    // Accounts always exposed
    //web3.eth.sendTransaction({/* ... */});
  } else {
    // Non-dapp browsers
    console.log(
      "Non-Ethereum browser detected. You should consider trying MetaMask!"
    );
  }
});

export default {
  data: function() {
    return {
      creator_id: "",
      top_creators: [],
      top_supporters: []
    };
  },
  methods: {
    lookup() {
      console.log(`Looking up ${this.creator_id}`);
      if (this.creator_id.startsWith("0x")) {
        // Creator is an Ethereum address
      } else {
        // Creator is an email address or profile URL
      }
    }
  }
};
</script>
