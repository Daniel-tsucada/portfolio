<template>
     <div class="context">
        <h1>{{typewriter}}</h1>
    </div>


<div class="area" >
            <ul class="circles">
                    <li></li>
                    <li></li>
                    <li></li>
                    <li></li>
                    <li></li>
                    <li></li>
                    <li></li>
                    <li></li>
                    <li></li>
                    <li></li>
            </ul>
    </div >
</template>

<script>
export default {
  name:'Hero',
  data () {
    return {
      typewriter: '',
      i: 0,
      timer: 0,
      str: '未経験フロントエンドエンジニア'
    }
},
mounted () {
  this.typeing()
},
methods: {
  typeing () {
    if (this.i <= this.str.length) {
      this.typewriter = this.str.slice(0, this.i++)
      this.timer = setTimeout(() => {
        this.typeing()
      }, 150)
   } else {
      clearTimeout(this.timer)
   }
 }
}

}
</script>

<style lang="scss" scoped>

*{
    margin: 0px;
    padding: 0px;
}


.context {
    width: 100%;
    position: absolute;
    top:50vh;

    h1{
    text-align: center;
    color: #fff;
    font-size: 50px;
    }
    
}


.area{
    background: rgba(15, 1, 1, 1);   
    width: 100%;
    height:100vh;
    
    .circles{
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;

    li{
    position: absolute;
    display: block;
    list-style: none;
    width: 20px;
    height: 20px;
    background: #0afea0;
    animation: animate 25s linear infinite;
    bottom: -150px;

    &:nth-child(1){
        left: 5%;	
        width: 150px;
        height: 150px;
        background: #0afea0;
        clip-path: polygon(50% 5%, 61% 40%, 98% 40%, 68% 62%, 79% 96%, 50% 75%, 21% 96%, 32% 62%, 2% 40%, 39% 40%);
        animation-delay: 0s;
    }

    &:nth-child(2){
      left: 10%;
      width: 20px;
      height: 20px;
      animation-delay: 2s;
      clip-path: polygon(50% 5%, 61% 40%, 98% 40%, 68% 62%, 79% 96%, 50% 75%, 21% 96%, 32% 62%, 2% 40%, 39% 40%);
      animation-duration: 12s;
    }

    &:nth-child(3){
      left: 70%;
      width: 20px;
      height: 20px;
      clip-path: polygon(50% 5%, 61% 40%, 98% 40%, 68% 62%, 79% 96%, 50% 75%, 21% 96%, 32% 62%, 2% 40%, 39% 40%);
      animation-delay: 4s;
    }

    &:nth-child(4){
      left: 40%;
      width: 60px;
      height: 60px;
      clip-path: polygon(50% 5%, 61% 40%, 98% 40%, 68% 62%, 79% 96%, 50% 75%, 21% 96%, 32% 62%, 2% 40%, 39% 40%);
      animation-delay: 0s;
      animation-duration: 18s;
    }

    &:nth-child(5){
      left: 65%;
      width: 40px;
      height: 40px;
      clip-path: polygon(50% 5%, 61% 40%, 98% 40%, 68% 62%, 79% 96%, 50% 75%, 21% 96%, 32% 62%, 2% 40%, 39% 40%);
      animation-delay: 0s;
    }

    &:nth-child(6){
    left: 75%;
    width: 110px;
    height: 110px;
    background: #0afea0;
    clip-path: polygon(50% 5%, 61% 40%, 98% 40%, 68% 62%, 79% 96%, 50% 75%, 21% 96%, 32% 62%, 2% 40%, 39% 40%);
    animation-delay: 3s;
    }

    &:nth-child(7){
      left: 35%;
      width: 150px;
      height: 150px;
      clip-path: polygon(50% 5%, 61% 40%, 98% 40%, 68% 62%, 79% 96%, 50% 75%, 21% 96%, 32% 62%, 2% 40%, 39% 40%);
      animation-delay: 7s;
    }

    &:nth-child(8){
    left: 50%;
    width: 25px;
    height: 25px;
    clip-path: polygon(50% 5%, 61% 40%, 98% 40%, 68% 62%, 79% 96%, 50% 75%, 21% 96%, 32% 62%, 2% 40%, 39% 40%);
    animation-delay: 15s;
    animation-duration: 45s;
    }

    &:nth-child(9){
    left: 20%;
    width: 30px;
    height: 30px;
    background: #0afea0;
    clip-path: polygon(50% 5%, 61% 40%, 98% 40%, 68% 62%, 79% 96%, 50% 75%, 21% 96%, 32% 62%, 2% 40%, 39% 40%);
    animation-delay: 2s;
    animation-duration: 35s;
    }

    &:nth-child(10){
    left: 90%;
    width: 150px;
    height: 150px;
    background: #0afea0;
    clip-path: polygon(50% 5%, 61% 40%, 98% 40%, 68% 62%, 79% 96%, 50% 75%, 21% 96%, 32% 62%, 2% 40%, 39% 40%);
    animation-delay: 0s;
    animation-duration: 11s;
    }
}
}
}

@media screen and (max-width:750px) { 
.context h1{
font-size: 30px;
}
}

@media screen and (max-width:450px) { 
.context h1{
font-size: 25px;
}
}
@media screen and (max-width:360px) { 
.context h1{
font-size: 20px;
}
}

@keyframes animate {

    0%{
        transform: translateY(0) rotate(0deg);
        opacity: 1;
        border-radius: 0;
    }

    100%{
        transform: translateY(-1000px) rotate(920deg);
        opacity: 0.5;
        border-radius: 50%;
    }

}
</style>