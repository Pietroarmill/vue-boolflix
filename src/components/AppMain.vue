<template>
  <main class="main">
    <div class="container ">
      <div class="main__card" v-for="item in movieArray" :key="item.id">
        <div class="image-box" style=" background-image: url('https://image.tmdb.org/t/p/w500/6aNKD81RHR1DqUUa8kOZ1TBY1Lp.jpg');">
          <div class="text-box">
            <p class="title">
              <span>Titolo:</span>
              {{ item.title }}
            </p>
            <p class="original-title">
              <span>Titolo originale:</span>
              {{ item.original_title }}
            </p>
            <p class="vote">
              <span>Voto:</span>
              {{ item.vote_average / 2 }}
            </p>
            <p class="overwiew">
              <span>Descrizione:</span>
              {{ item.overview }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "AppMain",
  props: ['movieArray'],
}
</script>


<style lang="scss" scoped>
@import "../style/common.scss";

.main {
  background-color: rgb(173, 230, 206);
  display: flex;
  padding: 2rem 0;
  align-items: center;

  .container {
    display: flex;
    flex-wrap: wrap;
  }

  &__card {
    width: calc(100% / 3 - 10px);
    min-height: 400px;
    margin: 1rem 5px;
    background-color: rgb(255, 249, 250);
  }

  .image-box {
    height: 100%;
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    .text-box {
      padding: 10px;
      span {
        font-weight: 600;
      }
    }
  }
}
</style>