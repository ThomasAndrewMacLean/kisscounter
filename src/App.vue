// src/App.vue

<template>
  <div class="container">
    <h1>{{ message }}</h1>
    <span class="kiss" v-for="(kiss,index) in kisses" v-bind:key="index">
      <div class="kiss1" @click="setKissedToTrue(index)">{{kiss}}</div>
    </span>

    <br>
    <button v-if="!kisses.includes('😘') && !kisses.includes('😛')" @click="resetKisses">Reset</button>
  </div>
</template>

<script>
let length = 25;
export default {
  name: "App",
  data() {
    return {
      message: "Kiss Counter",
      kisses:
        JSON.parse(localStorage.getItem("kisses")) ||
        Array.from({ length }, () => (Math.random() > 0.5 ? "😘" : "😛"))
    };
  },
  methods: {
    resetKisses() {
      this.kisses = Array.from({ length }, () =>
        Math.random() > 0.5 ? "😘" : "😛"
      );
      localStorage.setItem("kisses", JSON.stringify(this.kisses));
    },
    setKissedToTrue(index) {
      this.$set(this.kisses, index, "❌");
      localStorage.setItem("kisses", JSON.stringify(this.kisses));
    }
  }
};
</script>

<style scoped>
.container {
  width: 100vw;
  margin: 50px auto;
  text-align: center;
}

.kiss {
  font-size: 5rem;
  margin: 1rem;
  cursor: pointer;
}
.kiss1 {
  display: inline-flex;
}
</style>
