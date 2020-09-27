<template>
  <div id="app">
    <MainWrapper 
    :timersArray="timersArray"
    @add-new-timer="addNewTimer"/>
  </div>
</template>

<script>
import MainWrapper from './components/MainWrapper'

export default {
  name: 'App',
  data() {
    return {
       timersArray: []
    }
   
  },
  methods: {
    addNewTimer(){
      	this.timersArray.push({
         id: Math.random().toFixed(2),
        }); 
        console.log(this.arr);
      }
  },

  components: {
    MainWrapper
  },
}
</script>

