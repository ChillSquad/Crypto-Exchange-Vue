<script>
export default {
  props: {
    setCripto: {
      type: Function,
      required: true,
    },
  },
  data() {
    return {
      current: "",
    };
  },
  methods: {
    selectItem(val) {
      this.setCripto(val);
      this.current = val;
    },
  },
};
</script>

<template>
  <ul>
    <li @click="selectItem('BTC')" :class="current == 'BTC' ? 'active' : ''">
      Bitcoin
    </li>
    <li @click="selectItem('ETH')" :class="current == 'ETH' ? 'active' : ''">
      ETH
    </li>
    <li @click="selectItem('USDT')" :class="current == 'USDT' ? 'active' : ''">
      USDT
    </li>
  </ul>
</template>

<style scoped>
ul {
  font-size: 24px;
  list-style: none;
  width: 250px;
  display: block;
  margin: 20px auto 0 auto;
  border-radius: 3px;
  border: 1px solid #000;
}

li {
  color: #fff;
  cursor: pointer;
  padding: 5px;
  background: #24043e;
  transition: transform 500ms ease;
}

li:hover,
li.active {
  background: #1a032d;
  transform: scale(1.05);
}
</style>
