<template>
    <footer>
   <ul class="footer-menu">
      <li><router-link class="link" :to="{name: 'Home'}">Home </router-link></li>
      <li><router-link class="link" :to="{name: 'About'}">About </router-link></li>
      <li><router-link class="link" :to="{name: 'Blog'}">Blog </router-link></li>
    </ul>
    <p>© 2022 Daniel Tsucada</p>
  </footer>
</template>

<script>
export default {
name:'Footer'
}
</script>

<style lang="scss" scoped>
footer{
    width: 100%;
    height: 100px;
    background-color: #000000;
    color: white;
    text-align: center;
    margin-top: 0;

    ul.footer-menu li{
    display: inline;
    vertical-align: middle;
    padding-right: 5px;
    }

   .link {
        font-size: 14px;
        transition: .5s ease all;
        padding-bottom: 4px;
        text-decoration: none;
        color: #fff;

    &:hover {
    color: #0afea0;
    border-color: #0afea0;
    }
 }
}
</style>