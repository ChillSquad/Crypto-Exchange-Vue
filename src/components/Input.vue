<script>
export default {
  props: {
    changeAmount: {
      type: Function,
      required: true,
    },
    convert: {
      type: Function,
      required: true,
    },
  },
  data() {},
  methods: {},
};
</script>

<template>
  <input
    type="number"
    min="0"
    @input="changeAmount($event.target.value)"
    placeholder="Введите число"
  />
  <div>
    <button @click="convert()">Перевести</button>
  </div>
</template>

<style scoped>
input {
  border-radius: 5px;
  outline: none;
  border: none;
  padding: 10px;
  background: #fff;
  color: #333;
  font-size: 16px;
  margin-top: 20px;
  width: 255px;
}

button {
  margin-top: 30px;
  font-size: 18px;
  padding: 5px 10px;
  cursor: pointer;
  background: #fff;
  border: 0;
  border-radius: 5px;
  transition: transform 300ms ease;
}

button:hover {
  transform: translateY(-3px);
}

button:active {
  transform: scale(0.95);
}
</style>
