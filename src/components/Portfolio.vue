<template>
    <div class="portfolio">
    <h3>ポートフォリオ</h3>
  </div>
  <section class="about">

    <div class="about-left">
      <img src="../views/image.png" alt="">
    </div>

    <div class="about-right">
      <p>
      6ヶ月間プログラミングスクールに行っていた時に制作したサイトです。このサイトはフリーランスのフォトグラファーをイメージして制作したものです。このサイトには、html、css、jqueryを使用しています。最新の写真を簡単に入れ替えられるように、また、ブログで発信できるようにwordpressを組み込んでいます。
      </p>
      <a href="https://www.frontend-site.online">read more</a>
    </div>


  </section>
</template>

<script>
export default {
  name:'Portfolio',
     mounted() {
   const options = {
     root: null,
     rootMargin: "0px 0px -150px",
     threshold: 0
   }
   const images = document.querySelectorAll('.about')
   images.forEach((target) => this.onIntersect(target, options))
 },
 methods: {
   onIntersect(target, options = {}) {
     const observer = new IntersectionObserver(this.addShowClass, options)
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
.portfolio{
    text-align: center;
    -webkit-clip-path: polygon(0 0, 100% 0%, 100% 100%, 0% 50%);
    clip-path: polygon(0 0, 100% 0%, 100% 100%, 0% 50%);
    background-color: #000;
    padding-bottom: 20px;


    h3{
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

.about{
  max-width: 1080px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  margin: 0 auto;
  opacity: 0;
  transform: translateY(100px);
  transition: opacity 1.4s, transform 0.8s;
  padding: 80px 0;

  &.show{
       opacity: 1;
       transform: translateY(0);
  }

  &-left{
    flex-basis: 50%;

    img{
      max-width: 350px;
      padding: 0px;
    }
  }

  &-right{
    flex-basis: 50%;

    p{
      font-size: 18px;
      word-break: break-all;
    }

    a{
        display: inline-block;
        padding: 0.5em 1em;
        text-decoration: none;
        border-radius: 4px;
        color: #ffffff;
        background: #0afea0;
        box-shadow: 0px 2px 2px #0afea0;
        border-bottom: solid 3px #000302;
        margin-bottom: 30px;
        cursor: pointer;

        &:active{
            -webkit-transform: translateY(4px);
            transform: translateY(4px);
            box-shadow: 0px 0px 1px rgba(0, 0, 0, 0.2);
            border-bottom: none;
        }
    }
  }
}
</style>