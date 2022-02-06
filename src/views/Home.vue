<template>
  <Hero/>
  <Portfolio/>
  <Skill/>
</template>

<script>
import Hero from '../components/Hero'
import Portfolio from '../components/Portfolio'
import Skill from '../components/Skills'
export default {
  name:'Home',
  components:{
    Hero,

    Skill,

    Portfolio
  }

}
</script>

<style>

</style>