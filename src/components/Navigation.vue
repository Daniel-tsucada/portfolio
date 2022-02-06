<template>
<header :class="{'scrolled-nav': scrolledNav}">
  <nav>
    <div class="branding">
    <h1>DEVDEVELOPER</h1>
    </div>
    <ul v-show="!mobile" class="navigation" >
      <li><router-link class="link" :to="{name: 'Home'}" >Home</router-link></li>
      <li><router-link class="link" :to="{name: 'About'}">About</router-link></li>
      <li><router-link class="link" :to="{name: 'Blog'}">Blog</router-link></li>
    </ul>
      <div class="hamburger_btn"  v-on:click="toggleMobileNav" v-show="mobile" >
      <span class="line line_01" :class="{'btn_line01':mobileNav}"></span>
      <span class="line line_02" :class="{'btn_line02':mobileNav}"></span>
      <span class="line line_03" :class="{'btn_line03':mobileNav}"></span>
    </div>

    <transition name="mobile-nav">
          <ul v-show="mobileNav" class="dropdown-nav" v-on:click="mobileNav = false">
              <li><h1>DEVDEVELOPER</h1></li>
              <li><router-link class="link" :to="{name: 'Home'}" >Home</router-link></li>
              <li><router-link class="link" :to="{name: 'About'}">About</router-link></li>
              <li><router-link class="link" :to="{name: 'Blog'}">Blog</router-link></li>
          </ul>
  </transition>
  </nav>
</header>
</template>

<script>
export default {
  name:'navigation',
  data(){
    return {
      scrolledNav: null,
      mobile: null,
      mobileNav: null,
      windowWidth: null,
    };
  },
  created() {
    window.addEventListener('resize', this.checkScreen);
    this.checkScreen();
  },
  mounted(){
    window.addEventListener("scroll", this.updateScroll);
  },
  methods:{
    toggleMobileNav() {
      this.mobileNav = !this.mobileNav;
    },
    updateScroll() {
      const scrollPosition = window.scrollY;
      if(scrollPosition >50) {
        this.scrolledNav = true;
        return;
      }
      this.scrolledNav = false;
    },
    checkScreen() {
      this.windowWidth = window.innerWidth;
      if(this.windowWidth <= 750){
        this.mobile = true;
        return;
      }else{
      this.mobile = false;
      this.mobileNav = false;
      return;
      }

    },
  },
};
</script>

<style lang="scss" scoped>

header{
background-color: rgba(0, 0, 0, 0.8);
z-index: 99;
width: 100%;
position: fixed;
transition: .5s ease all;
color: #fff;

 nav{
 position: relative;
 display: flex;
 flex-direction: row;
 padding: 0;
 transition: 0.5s ease all;
 width: 90%;
 margin: 0 auto;
 @media (min-width: 1140px){
 max-width: 1140px;
 }

 ul,
 .link{
 font-weight: 500;
 color: #fff;
 list-style: none;
 text-decoration: none;
 }

 li {
 text-transform: uppercase;
 padding: 16px;
 text-decoration: none;
 }

 .link {
 font-size: 14px;
 transition: .5s ease all;
 padding-bottom: 4px;
 border-bottom: 1px solid transparent;

    &:hover {
    color: #0afea0;
    border-color: #0afea0;
    }
 }

 .branding {
 display: flex;
 align-items: center;

  h1{
  width: 50px;
  transition: .5s ease all;
   margin: 0;
   padding: 16px 0;
  }
 }



 .hamburger_btn{
 display: flex;
 align-items: center;
 position: absolute;
 top: 0px;
 right: 0px;
 cursor: pointer;
 z-index: 50;
 width: 60px;
 height: 70px;
 margin: 0;
 padding: 0;

  .line {
  position: absolute;
  top: 0;
  left: 15px;
  width: 30px;
  height: 2px;
  background: #0afea0;
  margin: 8px auto;
}


.line_01 {
  top: 16px;
  transition: 0.4s ease;
}
 .line_02 {
  top: 26px;
  transition: 0.4s ease;
}
.line_03 {
  top: 36px;
  transition: 0.4s ease;
}

.btn_line01 {
  transform: translateY(10px) rotate(-45deg);
  transition: 0.4s ease;
}
.btn_line02 {
  transition: 0.4s ease;
  opacity: 0;
}
.btn_line03 {
  transform: translateY(-10px) rotate(45deg);
  transition: 0.4s ease;
}

   
 }

 .navigation {
 display: flex;
 align-items: center;
 flex: 1;
 justify-content: flex-end;
 margin: 0;
 }





.dropdown-nav {
display: flex;
flex-direction: column;
position: fixed;
width: 100%;
max-width: 250px;
height: 100%;
background-color: black;
top: 0;
left: 0;
margin: 0;

  li {
  margin: 0;
  
  .link{
  color: #fff;
  }
  }
}

.mobile-nav-enter-active,
.mobile-nav-leave-active {
transition: 1s ease all;
}

.mobile-nav-enter-from,
.mobile-nav-leave-to {
transform: translateX(-250px);
}

.mobile-nav-enter-to {
transform: translateX(0);}

 }
}

.menu-enter-active, .menu-leave-active {
  transition: opacity 0.4s;
}
.menu-enter, .menu-leave-to {
  opacity: 0;
}
.menu-leave, .menu-enter-to{
  opacity: 1;
}

.scrolled-nav {
background-color: black;
box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);

  nav {
  padding: 8px 0;
  }
}



</style>