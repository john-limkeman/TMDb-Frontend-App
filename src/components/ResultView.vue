<template>
  <div>
      <h1>RESULTS</h1>
      <div v-for="result in results" v-bind:key="result.id">
          <img src="" alt="">
      </div>
  </div>
</template>

<script>
export default {
data(){
    return{

    }
},
props: ["results", "config"]
}
</script>

<style>

</style>