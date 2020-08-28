<template>
  <div id="app">
    <QR_Genarator/>
  </div>
</template>

<script>
import QR_Genarator from '@/components/QR_Genarator'
export default {
  name: 'App',
  components: {
    QR_Genarator
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
  margin-top: 60px;
}
</style>
