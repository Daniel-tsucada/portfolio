<template>
  <div class="experience">
  <h2>経歴</h2>
  </div>
  <main>
  <section class="timeline">
    <ul>
      <li v-for="(timeline, index) in timeline_data" v-bind:key="index" class="timeline-animation">
        <span></span>
        <div>{{ timeline.school }}</div>
        <div>{{ timeline.address }}</div>
        <div class="year">
          <span>{{ timeline.yearStart }}</span>
          <span>{{ timeline.yearEnd }}</span>
        </div>
      </li>
    </ul>
  </section>
</main>
</template>

<script>
export default {
name:'Experience',
  data: () => {
    return {
      timeline_data: [
        {
          "school":"芦屋国際中等教育学校",
          "address":"",
          "yearStart":"2012",
          "yearEnd":"2017"
        },
        {
          "school":"近畿大学",
          "address":"入学",
          "yearStart":"2018",
          "yearEnd":""
        },
                {
          "school":"プログラミングと出会う",
          "address":"6月からプログラミングスクールに入る。",
          "yearStart":"2021",
          "yearEnd":""
        },
                {
          "school":"近畿大学",
          "address":"卒業予定",
          "yearStart":"",
          "yearEnd":"2022"
        },
      ]
    }
  },
   mounted() {
   // rootからbottom:-150pxの位置で発火
   const options = {
     root: null,
     rootMargin: "0px 0px -150px",
     threshold: 0
   }
   const images = document.querySelectorAll('.timeline-animation')
   images.forEach((target) => this.onIntersect(target, options))
   const subTitles = document.querySelectorAll('.year')
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
.experience{
    text-align: center;
    -webkit-clip-path: polygon(0 0, 100% 0%, 100% 50%, 0% 100%);
    clip-path: polygon(0 0, 100% 0%, 100% 50%, 0% 100%);
    background-color: #000;
    padding-bottom: 20px;


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
main {
    max-width: 32em;
    height: 100%;
    margin: 1em auto;
    padding: 40px;
    border-radius: 4px;
    box-shadow: 0 5px 15px rgba(0,0,0,.5);
}
.timeline {
  padding: 5px 45px;
  ul {
    position: relative;
    &::before {
      height: 100%;
    }
  }
  li {
    position: relative;
    margin: 60px 35px;
    width: 100%;
    list-style: none;
    line-height: 25px;
    &>span {
      position: absolute;
      left: -35px;
      height: 110%;
      border: 2px solid yellow ;
    }
    &>span::before, &>span::after {
      width: 14px;
      height: 14px;
      left: -7px;
    }
    &>span::before {
      top: -15px;
    }
    &>span::after {
      top: 100%;
    }
    div {
      &:nth-child(2) {
        font-size: 1.2em;
      }
      &:nth-child(3), &:nth-child(4) {
        font-size: 1em;
        font-style: italic;
      }
    }
    
    .year span {
      position: absolute;
      font-size: 1em;
      left: -85px;
      width: 40px;
      text-align: right;
      &:first-child {
        top: -20px;
      }
      &:last-child {
        top: 100%;
      }
    }

  }

  &-animation{
    opacity: 0;
    transform: translateX(-100px);
    transition: opacity 1.4s, transform 0.8s;

     &.show {
      opacity: 1;
      transform: translateX(0);
     }
  }
}
</style>