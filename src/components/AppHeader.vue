<template>
  <header class="header">
    <div class="container">
      <div class="header__search">
        <input
          type="text"
          placeholder="Search"
          v-model="textSearch"
          @keyup.enter="$emit('searchClick', textSearch)"
        >
        <button @click="$emit('searchClick', textSearch)">Cerca</button>
      </div>
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
    }
  },
};
</script>


<style lang="scss" scoped>
@import "../style/common.scss";

.header {
  background-color: lightblue;
  height: 100px;
  display: flex;
  align-items: center;
}
</style>