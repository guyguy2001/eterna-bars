<template>
  <div>
    <bar1></bar1>
    <br />
    <br />
    <bar2></bar2>
  </div>
</template>
<script>
  import bar1 from './Bar1'
  import bar2 from './Bar2'
  export default {
    name: 'app',
    components: { bar1, bar2 },
    data() {
      return {
      }
    }
  }
</script>
<style>
  body {
    background-color: #011e46;
    text-align: center;
    color: white;
    font-family: 'Helvetica Neue', 'Open Sans', 'Arial', 'sans-serif';
  }
</style>