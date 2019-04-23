<template>
  <div class="counter-warp">
    <i-row><i-col span="24" i-class="col-class">Vuex counter：{{ count }}</i-col></i-row>  
    <i-row>
    <i-col span="12"><button @click="increment" hover-class="hover">+</button></i-col>
    <i-col span="12"><button @click="decrement" hover-class="hover">-</button></i-col>
    </i-row>  
  </div>
</template>

<script>
// Use Vuex
import card from '@/components/card'
import store from './store'

export default {
  computed: {
    count () {
      return store.state.count
    }
  },
  methods: {
    increment () {
      store.commit('increment')
    },
    decrement () {
      store.commit('decrement')
    }
  }
}
</script>

<style>
.counter-warp {
  text-align: center;
  margin-top: 100px;
}
.home {
  display: inline-block;
  margin: 100px auto;
  padding: 5px 10px;
  color: blue;
  border: 1px solid blue;
}
.hover {
  color: aqua;
  background-color: red;

}
.col-class {
  border: 1px solid #98bf21;
}
</style>
