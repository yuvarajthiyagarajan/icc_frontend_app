<template>
  <div id="app">
  <JobsList />
  </div>
</template>

<script>
import JobsList from './components/JobsList'
export default {
    name: "App",
    components: {
       JobsList
    }
}
</script>

<style>
body{
  background-color: rgb(66, 66, 66);
  color: aliceblue;
}
</style>