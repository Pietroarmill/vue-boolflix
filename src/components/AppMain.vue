<template>
  <main class="main">
    <div class="container ">
      <div class="main__card" v-for="item in movieArray" :key="item.id">
        <div class="image-box">
          <img class="poster" :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`" alt="">
          <div class="text-box">
            <div class="title">
              <span>Titolo: </span>
              <p>{{ item.title || item.name }}</p>
            </div>
            <div class="original-title">
              <span>Titolo originale: </span>
              <p>{{ item.original_title || item.original_name }}</p>
            </div>
            <div class="language">
              <span>Lingua: </span>
              <!-- <img src="../assets/img/en.jpg" alt=""> -->
              <img v-if="item.original_language === 'en'" src="../assets/img/en.jpg" alt="">
              <img v-else-if="item.original_language === 'it'" src="../assets/img/it.jpg" alt="">
              <img v-else-if="item.original_language === 'fr'" src="../assets/img/Flag_of_France.png" alt="">
              <img v-else-if="item.original_language === 'sv'" src="../assets/img/sweden.jpg" alt="">
              <span v-else>{{ item.original_language }}</span>
            </div>
            <div class="vote">
              <span>Voto: </span>
              <small v-if="item.vote_average / 2 < 0.5">
                <i class="far fa-star"></i>
                <i class="far fa-star"></i>
                <i class="far fa-star"></i>
                <i class="far fa-star"></i>
                <i class="far fa-star"></i>
              </small>
              <small v-else-if="item.vote_average / 2 < 1.5">
                <i class="fas fa-star"></i>
                <i class="far fa-star"></i>
                <i class="far fa-star"></i>
                <i class="far fa-star"></i>
                <i class="far fa-star"></i>
              </small>
              <small v-else-if="item.vote_average / 2 < 2.5">
                <i class="fas fa-star"></i>
                <i class="fas fa-star"></i>
                <i class="far fa-star"></i>
                <i class="far fa-star"></i>
                <i class="far fa-star"></i>
              </small>
              <small v-else-if="item.vote_average / 2 < 3.5">
                <i class="fas fa-star"></i>
                <i class="fas fa-star"></i>
                <i class="fas fa-star"></i>
                <i class="far fa-star"></i>
                <i class="far fa-star"></i>
              </small>
              <small v-else-if="item.vote_average / 2 < 4.5">
                <i class="fas fa-star"></i>
                <i class="fas fa-star"></i>
                <i class="fas fa-star"></i>
                <i class="fas fa-star"></i>
                <i class="far fa-star"></i>
              </small>
              <small v-else>
                <i class="fas fa-star"></i>
                <i class="fas fa-star"></i>
                <i class="fas fa-star"></i>
                <i class="fas fa-star"></i>
                <i class="fas fa-star"></i>
              </small>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "AppMain",
  props: {
    movieArray: Array,
  }
};
</script>


<style lang="scss" scoped>
@import "../style/common.scss";
@import '~@fortawesome/fontawesome-free/css/all.min.css';

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
    width: calc(100% / 4 - 10px);
    margin: 1rem 5px;
    max-width: 342px;
    background-color: #000000;

    .image-box {
      .poster {
        display: block;
      }
      
      .text-box {
        color: white;
        padding: .8rem;
        display: none;

        div {
          margin: .5rem 0;
        }

        span {
          font-weight: 600;
        }

        p {
          display: inline-block;
        }

        img {
          width: 1rem;
          height: 1rem;
          border-radius: 50%;
          vertical-align: middle;
        }

        .vote small {
          color: yellow;
        }
      }
    }
  }
}

// Hover
.main__card:hover .poster {
  display: none;
}

.main__card:hover .text-box {
  display: block;
}
</style>