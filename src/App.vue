// src/App.vue

<template>
  <div class="container">
    <h1>{{ message }}</h1>
    <span class="kiss" v-for="(kiss,index) in kisses" v-bind:key="index">
      <div class="kiss1" @click="setKissedToTrue(index)">{{kiss}}</div>
    </span>

    <br>
    <button @click="resetKisses">Reset</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      message: "Kiss Counter",
      kisses: Array.from({length: 40}, () => Math.random()>0.5? "😘":"😛");
    };
  },
  methods: {
    resetKisses() {
      this.kisses =  Array.from({length: 40}, () => Math.random()>0.5? "😘":"😛");
    },
    setKissedToTrue(index) {
      this.$set(this.kisses, index, "❌");
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
