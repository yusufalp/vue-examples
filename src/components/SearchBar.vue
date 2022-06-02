<template>
  <div class="container">
    <input v-model="searchTerm" placeholder="Search videos"/>
    <button @click="onClick" type="button">Search</button>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    onClick: function() {
      this.$emit("searchTermChange", this.searchTerm);
    }
  }
}
</script>

<style scoped>

.container {
  display: flex;
}
input {
  width: 100%;
  flex: 10;
}
button {
  flex: 2;
}
</style>