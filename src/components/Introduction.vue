<template>
    <section class="grid feature-grid-1">
    <div class="bg1 mobile-none show-on-desktop"></div>
    <div class="img1">
      <img src="../image/image1.png" alt="">
    </div>
    <div class="feature-text feature-desc-01">
      <h4 class="subtitle">DANIEL TSUCADA</h4>
      <p>プログラミングを始めて約8ヶ月です。６ヶ月間プログラミングスクールのオンラインのコースを受講していました。その6ヶ月間では、HTML,CSS,JAVASCRIPTをメインに勉強し、PHPも少し勉強しました。現在はVue.jsを勉強しています。</p>
    </div>
   </section>
</template>

<script>
export default {
  name:'Introduction'

}
</script>

<style lang="scss" scoped>


.grid img {
     width:100%; 
  height: 100%; 
    box-shadow: -5px 5px 10px rgba(35,41,95,0.3);

    .mobile-none {
      display:none;
    }
  }

section {
  width:100%;
  
}

p {
  font-size:1.7rem;
  line-height:2.3rem;
  letter-spacing:0.05rem;
  color:#4c4c4c;
  margin-bottom:1.7rem;
}
.grid {
  display:inline-block;
  margin: 0;
  padding: 0;
}
.grid > div {
  flex:1;
  padding:20px;
}
.feature-text {
  position:relative;
}
.feature-text::before {
  content:"";
  width:100px;
  height:3px;
  background:gold;
  position:absolute;
  top:0;
}

.subtitle {
  font-size:3.5rem;
  margin-bottom:1.2rem;
  padding:0;
  color: #0afea0;
}





@media screen and (min-width:768px) {
  .grid {
    display:grid;

    & > div{
      padding:0;
    }

  .show-on-desktop {
    display:block;
  }
  .bg1 {
    background: #0afea0;
    height:300px;
    grid-column: 2 / 4;
    grid-row: 2 / 4;
  }
  .img1 {
    grid-column: 3 / 5;
    grid-row: 3 / 5;
  }

  .feature-desc-01 {
    grid-column: 6;
    grid-row: 3;
    position:relative;

    &::before{
    content:"";
    width:100px;
    height:3px;
    background:gold;
    position:absolute;
    left: -50px;
    }
  }
  }
  
  .feature-grid-1 {
    grid-template-columns: 1fr 2fr 6fr 2fr 1fr 10fr 2fr;
    grid-template-rows: 80px 80px 200px 100px auto minmax(100px, 200px);
  }

}
</style>