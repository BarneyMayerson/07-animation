<template>
  <button type="button" @click="flag = !flag">Toggle</button>

  <transition name="fade">
    <h2 v-if="flag">Hello there...</h2>  
  </transition>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      flag: false,
    }
  },
}
</script>

<style scoped>
.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: all 1s linear;
}

.fade-leave-to {
  transition: all .5s linear;
  opacity: 0;
}
</style>


