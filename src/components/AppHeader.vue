<template>
  <header class="header">
    <div class="container">
      <section class="header__section">
        <div class="box-logo">
          <h1>
            <span>B</span>
            <span class="letter2">O</span>
            <span class="letter3">O</span>
            <span class="letter4">L</span>
            <span class="letter4">F</span>
            <span class="letter3">L</span>
            <span class="letter2">I</span>
            <span>X</span>
          </h1>
        </div>
        <div class="header__search">
          <label for="search">
            <i class="fas fa-search"></i>
          </label>
          <input id="search" type="text" placeholder="Search" v-model="textSearch"
            @keyup.enter="$emit('searchClick', textSearch)">
          <button @click="$emit('searchClick', textSearch)">Cerca</button>
        </div>
      </section>
    </div>
  </header>
</template>

<script>
export default {
  name: "AppHeader",
  data() {
    return {
      textSearch: '',
    };
  },
  methods: {
    searchClick() {
      console.log(this.textSearch);
    },
  },
};
</script>


<style lang="scss" scoped>
@import "../style/common.scss";
@import '~@fortawesome/fontawesome-free/css/all.min.css';

.header {
  background-color: #141414;
  height: 100px;
  display: flex;
  align-items: center;

  &__section {
    display: flex;
    justify-content: space-between;
    align-items: center;

    .box-logo {
      color: red;
      font-size: 1.8rem;

      h1 {
        span {
          vertical-align: middle;
        }

        .letter2 {
          font-size: 2.3rem;
        }

        .letter3 {
          font-size: 2rem;
        }

        .letter4 {
          font-size: 1.7rem;
        }
      }
    }
  }

  &__search {
    color: white;

    input {
      height: 1.5rem;
      background-color: transparent;
      color: white;
      border: 1px solid white;
      padding: 10px;
      margin: 0 .7rem;
    }

    button {
      background-color: transparent;
      color: white;
      border: 1px solid white;
      padding: .19rem .5rem;
    }
  }
}
</style>