<template>
  <div class="main">
    <h1>Welcome to the book searcher !!!</h1>
    <div class="search">
      <input
        type="text"
        placeholder="Search for books, tutorials, manuals and authors"
        v-model="bookInput"
      />
      <button @click="loadData">Find books</button>
    </div>
    <div class="result">
      <div v-for="item in data.items" :key="item.id">
        <Bookself
          :thumbnail="item.volumeInfo.imageLinks.thumbnail"
          :title="item.volumeInfo.title"
          :page-count="item.volumeInfo.pageCount"
          :published-date="item.volumeInfo.publishedDate"
          :authors="item.volumeInfo.authors"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Bookself from "~/components/Bookself.vue";

export default {
  data() {
    return {
      data: [],
      bookInput: "",
    };
  },
  methods: {
    loadData() {
      let query = this.bookInput;
      axios
        .get(`https://www.googleapis.com/books/v1/volumes?q=${query}`)
        .then((response) => (this.data = response.data));
    },
  },
  components: { Bookself },
};
</script>

<style scoped>
.main {
  max-width: 1200px;
  margin: 0 auto;
}

h1 {
  text-align: center;
  font-family: sans-serif;
}

.search {
  text-align: center;
}

.search input {
  padding: 0.4rem 0.8rem;
  width: 400px;
}

.search button {
  padding: 0.4rem 0.8rem;
}
</style>
