<template>
  <button :class="color">{{ name }}</button>
</template>

<script>
export default {
  name: "Button",
  props: {
    name: String,
    color: String,
  },
};
</script>

<style scoped>
.green {
  padding: 5px;
  font-weight: bold;
  background-color: rgb(85, 117, 38);
  color: white;
  border: 0;
  border-radius: 5px;
  margin: 0 5px;
  cursor: pointer;
}

.red {
  padding: 5px;
  font-weight: bold;
  background-color: red;
  color: white;
  border: 0;
  border-radius: 5px;
  margin: 0 5px;
  cursor: pointer;
}

.yellow {
  padding: 5px;
  font-weight: bold;
  background-color: rgb(216, 216, 31);
  color: white;
  border: 0;
  border-radius: 5px;
  margin: 0 5px;
  cursor: pointer;
}
</style>
