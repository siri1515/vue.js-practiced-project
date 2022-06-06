<template>
  <div id="app">
    <app-header />
    <br><br><br>
    <app-card 
      v-if="results.length>0"
      :currentResultList="results[index]"
      :nextResultList="nextResultList"
      :previousResultList="previousResultList"
      />
  </div>
</template>

<script>
import appHeader from './components/appHeader.vue'
import appCard from './components/appCard.vue'

export default {
  name: 'App',
  components: {
    appHeader,
    appCard
  },

  data(){
    return{
      results: [],
      index: 0,
    }
  },

  methods: {
    nextResultList(){
      this.index++
    },

    previousResultList(){
      this.index--
    },

    backIndexCheck(){
      if(this.index == 0){
          return true
      }
      else
      {
          return false
      }
    },

    nextIndexCheck(){
      if(this.index == this.results.length-1){
          return true
      }
      else
      {
          return false
      }
    }
  },

  mounted: function(){
    fetch('https://opentdb.com/api.php?amount=10&category=15&difficulty=medium&type=multiple',
    {
      method:'get'
    })

      .then((response) => {
        return response.json()
      })

      .then((jsonData) => {
        this.results = jsonData.results
      })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color:lightblue;
  height: 100vh;
}

</style>
