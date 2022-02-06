<template>
  <div class="hero">
    <div class="container hero__container">
        <img  class="hero__image">
        <h1 class="hero__title" v-html="article.title"></h1>
    </div>
  </div>
<div class="container-2">
    <p v-html="article.content"></p>
</div>

</template>

<script>
import axios from 'axios'
export default {

  data: () => ({
    article: {}
  }),


  async mounted() {
    const response = await axios.get(
      "https://blog-dev.microcms.io/api/v1/article/" +
        this.$route.params.id,
      {
        headers: { "X-MICROCMS-API-KEY": process.env.VUE_APP_X_MICROCMS_API_KEY }
      }
    );
    this.article = response.data;
  }
};

</script>

<style lang="scss" scoped>
.container {
  width: 100%;
  max-width: 1080px;
  margin-left: auto;
  margin-right: auto;
  display: flex;
  flex-direction: column;


}

.hero {
  position: relative;
  display: flex;
  align-items: flex-end;
  margin-bottom: 3rem;
  background: radial-gradient(#F2B9A1, #EA6264);
  
  &::before,
  &::after {
      content: '';
  }

  &::before {
      float: left;
      height: 40vh;
      min-height: 320px;
      max-height: 640px;
  }

  &::after {
      display: table;
      clear: both;
  }
}

.hero__container {
  padding: 3rem;
}

.hero__image {
  position: absolute;
  z-index: 1;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.hero__title {
  margin: 0;
  color: #fff;
  font-size: 3rem;
}

.container-2{
  width: 100%;
  max-width: 1080px;
  margin: auto;
  padding: 0 20px;
  min-height: 100vh;

  
  p{
    height: 100%;
    margin-bottom: 20px;
  }
}

*{
  padding: 0;
  margin: 0;
}
</style>