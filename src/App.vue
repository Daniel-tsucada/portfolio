<template>
<Navigation/>
  <router-view/>
  <Footer/>
</template>

<script>
import Navigation from './components/Navigation'
import Footer from './components/Footer'
export default {
  name:'App',
  components:{
    Navigation,
    Footer
  }
  
}
</script>

<style lang="scss">
*{
padding: 0;
margin: 0;
box-sizing: border-box;
}

body{
  color: #fff;
  background: #111;
}
</style>
