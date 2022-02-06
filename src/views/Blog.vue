<template>
<section>
      <div  class="cards">
      <div v-for="article in articles" :key="article.id" class="card card-1">
        <div class="container">
          <img :src="article.image.url">
        </div>
        <div class="details">
            <h1 v-html="article.title"></h1>
            <p v-html="article.summary"></p>
            <a><router-link :to="{ name: 'Post', params: { id: article.id } }">more</router-link></a>
        </div>
      </div>
      </div>
</section>
</template>

<script>
import axios from "axios";

export default {
  name: "Home",

  data: () => ({
    articles: []
  }),

  async mounted() {
    // 記事を取得する
    const response = await axios.get(
      "https://blog-dev.microcms.io/api/v1/article",
      {
        headers: { "X-MICROCMS-API-KEY": process.env.VUE_APP_X_MICROCMS_API_KEY }
      }
    );
    this.articles = response.data.contents;
  }
};

</script>

<style style lang="scss" scoped>
*{
padding: 0;
margin: 0;
box-sizing: border-box;

}


section {
display: grid;
place-items: center center;
max-width: 1080px;
margin: auto;
display: flex;
flex-direction: column;
min-height: 100vh;
padding-top: 80px;

 .cards{
display: grid;
grid-template-columns: repeat(auto-fit,minmax(300px ,1fr));
padding: 20px;
grid-gap: 40px;

.card{
background-color: #c1c1cb29;
border-radius: 20px;
box-shadow: 0 0 10px ;
transition:box-shadow 0.3s;

  &:hover{
  box-shadow:0 0 30px rgb(0, 110, 255, 0.5), 0 2px 5px rgba(0, 0, 0, 0.3);
  transform:translate(0, -2px);
  }
}

.container {
position: relative;
clip-path: polygon( 0 0,100% 0, 100% 85%, 0 100%);

  img{
width: 100%;
display: block;
border-radius: 20px 20px 0 0;
}
}
.details{
display: block;
word-wrap: break-word;
text-align: center;

 a{
 text-decoration: none;
 color: #fff;
   &:hover{
   color: #0afea0;
   }
 }

 p{
  text-align: left;
  padding: 5px;
 }
}
}
}

</style>