<template>
  <div class="book">
    <div class="book-img">
      <img :src="thumbnail" alt="" />
    </div>
    <div class="book-info">
      <h2>{{ title }}</h2>
      <div class="book-authors">
        <span class="authors">
          {{ authors ? "By " + authors.join(", ") : "" }}</span
        >
      </div>
      <div class="book-extra">
        <span class="pageCount">{{ pageCount }} pages | </span>
        <span class="publishedDate">{{ publishedDate }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["thumbnail", "title", "pageCount", "publishedDate", "authors"],
};
</script>

<style scoped>
.book {
  display: flex;
  width: 800px;
  margin: 1rem auto;
  background: rgb(228, 228, 228);
}
.book-img {
  flex: 1;
}

.book-info {
  flex: 4;
}

.book-info h2 {
  margin: 1rem 0;
}

.authors {
  font-weight: bold;
  color: rgb(120, 43, 193);
}

.book-extra {
  margin: 1rem 0;
}
</style>
