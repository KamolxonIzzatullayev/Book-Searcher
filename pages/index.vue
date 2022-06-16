<template>
  <div>
    <input type="text" v-model="idParam"/>
    <button @click="goToId">Go</button>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      idParam: ''
    }
  },

  methods: {
    goToId() {
      this.$router.push('/about/' + this.idParam)
    }
  },
};
</script>
