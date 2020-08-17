<template>
  <div id="app">
    <button class="btn btn-primary m-5" @click="addItem"> Add Item </button>
    <div class="d-flex flex-column justify-content-center align-items-center">

        <!-- <transition appear 

        appear-active-class=""
        appear-class=""
        appear-to-class=""

        enter-class="my-enter" 
        enter-active-class="animated animate__bounceIn" 
        enter-to-class="my-enter-to"

        @before-enter="beforeEnter"
        @enter="enter"
        @after-enter="afterEnter"
        @enter-cancelled="enterCancelled"
        >
        -->

        <transition-group appear mode="out-in" name="fade" tag="ul" class="list-group">
            <li class="list-group-item" @click="dropItem(index)" v-for="(nbr, index) in data" :key="nbr"> {{ nbr }} </li>
        </transition-group>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      data: [1, 2, 3, 4, 5],
      display: true,
      componentSelected: 'Ca'
    }
  },
  methods: {
    dropItem(index) {
      this.data.splice(index, 1);
    },
    addItem() {
      this.data.splice(Math.floor( Math.random * this.data.length ), 0, this.data.length);
    }
    /*
    beforeEnter(el) {
      console.log('in before enter')
    },
    enter(el, done) {
      console.log('in enter')
    },
    afterEnter(el) {
      console.log('after enter')
    },
    enterCancelled(el) {
      console.log('enter cancelled')
    }*/
  },
}
</script>

<style scoped>
  @keyframes fade-in {
    0% {
      opacity: 0;
      filter: grayscale(100%);
      transform: translateX(-20px);
    }
    25% {
      transform: translateX(10px);
    }
    50% {
      transform: translateX(-5px);
    }
    75% {
      transform: translateX(-3px);
    }
    100% {

    }
  }

  .fade-move {
    transition: all 2s;
  }

  .fade-enter {
    opacity: 0;
    filter: grayscale(100%);
    transform: translateX(-20px);
  }

  .fade-enter-to {

  } 

  .fade-enter-active {
    /* transition: all 2s; */
    animation: fade-in 4s;
  }

  .fade-leave {
    
  }

  .fade-leave-to {
    opacity: 0;
    transform: translateX(20px);
  }

  .fade-leave-active {
    position: absolute;
    transition: all 2s;
  }
</style>
