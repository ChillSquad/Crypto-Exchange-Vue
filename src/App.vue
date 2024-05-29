<script>
import Input from "./components/Input.vue";
import Selector from "./components/Selector.vue";
import CryptoConvert from "crypto-convert";

const convert = new CryptoConvert(/*options?*/);

export default {
  components: { Input, Selector },
  data() {
    return {
      amount: 0,
      criptoFirst: "",
      criptoSecond: "",
      error: "",
      result: 0,
    };
  },
  methods: {
    changeAmount(val) {
      this.amount = val;
    },
    setCriptoFirst(val) {
      this.criptoFirst = val;
    },
    setCriptoSecond(val) {
      this.criptoSecond = val;
    },
    async convert() {
      if (this.amount <= 0) {
        this.error = "Ошибка ввода!";
        /* Чтобы дальнейший код не срабатывал */
        alert(this.error);
        return;
      } else if (this.criptoFirst == "" || this.criptoSecond == "") {
        this.error = "Выберите валюту!";
        alert(this.error);
        return;
      } else if (this.criptoFirst == this.criptoSecond) {
        this.error = "Ошибка!";
        alert(this.error);
        return;
      }
      this.error = "";

      await convert.ready(); //Wait for the initial cache to load
      if (this.criptoFirst == "BTC" && this.criptoSecond == "ETH") {
        this.result = convert.BTC.ETH(this.amount);
      } else if (this.criptoFirst == "BTC" && this.criptoSecond == "USDT") {
        this.result = convert.BTC.USDT(this.amount);
      } else if (this.criptoFirst == "ETH" && this.criptoSecond == "BTC") {
        this.result = convert.ETH.BTC(this.amount);
      } else if (this.criptoFirst == "ETH" && this.criptoSecond == "USDT") {
        this.result = convert.ETH.USDT(this.amount);
      } else if (this.criptoFirst == "USDT" && this.criptoSecond == "ETH") {
        this.result = convert.USDT.ETH(this.amount);
      } else if (this.criptoFirst == "USDT" && this.criptoSecond == "BTC") {
        this.result = convert.USDT.BTC(this.amount);
      }
    },
  },
};
</script>

<template>
  <a href="index.html" class="main_link">
    <h1>CRIPTO</h1>
  </a>
  <Input :changeAmount="changeAmount" :convert="convert" />
  <p v-show="result != 0" class="resultClass">{{ result }}</p>
  <div class="selectors">
    <Selector :setCripto="setCriptoFirst" />
    <Selector :setCripto="setCriptoSecond" />
  </div>
</template>

<style scoped></style>
