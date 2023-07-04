<template>
  <!-- <button type="button" @click="flag = !flag">Toggle</button> -->

  <!-- <Transition name="fade" mode="out-in">
    <h2 v-if="flag" key="main">Hello there...</h2>  
    <h2 v-else key="secondary">Hello from here...</h2>  
  </Transition> -->

  <!-- <Transition name="zoom" type="animation" appear>
    <h2 v-if="flag">Hey! You!</h2>  
  </Transition> -->

  <!-- <Transition
    @before-enter="onBeforeEnter"
    @enter="onEnter"
    @after-enter="onAfterEnter"
    @before-leave="onBeforeLeave"
    @leave="onLeave"
    @after-leave="onAfterLeave"
    :css="true"
    name="fade"
  >
    <h2 v-if="flag">Hey!</h2>
  </Transition> -->

  <button type="button" @click="addItem">Add</button>
  <ul>
    <TransitionGroup name="fade">
      <li 
        v-for="(number, index) in numbers" 
        :key="number"
        @click="removeItem(index)"
      >
        {{ number }}
      </li>
  </TransitionGroup>
  </ul>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      flag: true,
      numbers: [1, 2, 3, 4, 5],
    }
  },

  methods: {
    addItem() {
      const num = Math.floor(Math.random() * 100 + 1);
      const index = Math.floor(Math.random() * this.numbers.length);

      this.numbers.splice(index, 0, num);
    },
    removeItem(index) {
      this.numbers.splice(index, 1);
    },

    onBeforeEnter(el) {
      console.log("on-before-enter fired", el);
    },
    onEnter(el) {
      // const animation = el.animate([
      //   { transform: "scale3d(0, 0, 0)" }, 
      //   {},
      // ], {
      //   duration: 1000,
      // });

      // animation.onfinish = () => {
      //   // alert("Enter is done");
      //   done();
      // }
    },
    onAfterEnter(el) {
      console.log("on-after-enter fired", el);
    },
    onBeforeLeave(el) {
      console.log("on-before-leave fired", el);
    },
    onLeave(el) {
      // const animation = el.animate([
      //   {},
      //   { transform: "scale3d(0, 0, 0)" }, 
      // ], {
      //   duration: 1000,
      // });

      // animation.onfinish = () => {
      //   // alert("Leave is done");
      //   done();
      // }
    },
    onAfterLeave(el) {
      console.log("on-after-leave fired", el);
    },
  },
}
</script>

<style scoped>
li {
  font-size: 24px;
  cursor: pointer;
}

h2 {
  width: 400px;
  padding: 20px;
  margin: 20px;
}
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

.zoom-enter-active {
  animation: zoom-in 1s linear forwards;
  transition: all 1s linear;
}

.zoom-leave-active {
  animation: zoom-out 1s linear forwards;
  transition: all 1s linear;
}

.zoom-enter-from,
.zoom-leave-to {
  opacity: 0;
}

@keyframes zoom-in {
  from {
    transform: scale(0, 0);
  }
  to {
    transform: scale(1, 1);
  }
}

@keyframes zoom-out {
  from {
    transform: scale(1, 1);
  }
  to {
    transform: scale(0, 0);
  }
}
</style>


