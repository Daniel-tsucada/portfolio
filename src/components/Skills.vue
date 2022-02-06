<template>
  <div class="skills">
    <h2>My skills</h2>
  </div>
  <section>
    <div class="skill">
      <div class="skill-container">
        <i class="fab fa-html5"></i>
      </div>
      <h1 class="nome">HTML</h1>
      <p></p>
    </div>

    <div class="skill">
      <div class="skill-container">
        <i class="fab fa-css3-alt"></i>
      </div>
      <h1 class="nome">CSS</h1>
    </div>

    <div class="skill">
      <div class="skill-container">
        <i class="fab fa-js"></i>
      </div>
      <h1 class="nome">JAVASCRIPT</h1>
    </div>

    <div class="skill">
      <div class="skill-container">
        <i class="fas fa-file-code"></i>
      </div>
      <h1 class="nome">JQUERY</h1>
    </div>

    <div class="skill">
      <div class="skill-container">
        <i class="fab fa-vuejs"></i>
      </div>
      <h1 class="nome">VUE JS</h1>
    </div>

    <div class="skill">
      <div class="skill-container">
        <i class="fab fa-wordpress"></i>
      </div>
      <h1 class="nome">WORDPRESS</h1>
    </div>
  </section>
</template>

<script>
export default {
  name:'Skill',
 mounted() {
   // rootからbottom:-150pxの位置で発火
   const options = {
     root: null,
     rootMargin: "0px 0px -150px",
     threshold: 0
   }
   const images = document.querySelectorAll('.skill')
   images.forEach((target) => this.onIntersect(target, options))
   const subTitles = document.querySelectorAll('.nome')
   subTitles.forEach((target) => this.onIntersect(target, options))
 },
 methods: {
   onIntersect(target, options = {}) {
     const observer = new IntersectionObserver(this.addShowClass, options)
     // 監視したい要素をobserveする。
     observer.observe(target)
   },
   addShowClass(entries) {
     for(const e of entries) {
       if (e.isIntersecting) {
         e.target.classList.add("show")
       }
     }
   }
 }
}


</script>

<style lang="scss" scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.skills{
    text-align: center;
    -webkit-clip-path: polygon(0 0, 100% 0%, 100% 50%, 0% 100%);
    clip-path: polygon(0 0, 100% 0%, 100% 50%, 0% 100%);
    background-color: #000;
    height: 100%;


    h2{
      display: block;
      position: relative;
      width: 140px;
      margin:0 auto ;
      margin-bottom: 5px;
      color: #fff;

      &::before{
        content: '';
        height: 3px;
        background-color: #0afea0;
        position: absolute;
        top: 0;
        bottom: 0;
        margin: auto;
        z-index: -1;
        width: 300px;
        left: -75px;
      }
    }
}

section{
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  text-align: center;
  max-width: 1080px;
  margin:0 auto;
  padding-top: 15px;

  .skill{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 100px;
    opacity: 0;
    transform: translateX(-100px);
    transition: opacity 1.4s, transform 0.8s;

     &.show {
       opacity: 1;
       transform: translateX(0);
     }

     h1{
      letter-spacing: 2px;
    }

    &-container{
      width: 100px;
      height: 100px;
      clip-path: polygon(50% 0%, 100% 38%, 82% 100%, 18% 100%, 0% 38%);
      background-color: #000;
      margin-bottom: 2rem;
      display: flex;


      &:hover{
        opacity: 0.7;
        transition: 0.5s ;
      }

      i{
        color: #0afea0;
        font-size: 50px;
        margin: auto;
        padding: 0;
      }
    }
      .nome  {
     opacity: 0;
     transform: translateX(100px);
     transition: opacity 1.4s, transform 0.8s;

     &.show {
       opacity: 1;
       transform: translateX(0);
     }
   }

  }
}


</style>