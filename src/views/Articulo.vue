<template>
  <Titulo txt="Articulo Pages" />
  <div>{{item.title}}</div>
  <div>{{item.body}}</div>
</template>

<script>
import Titulo from "../components/Titulo";
export default {
  components: {
    Titulo,
  },
  methods: {
    async consumeApi() {
      try {
        const data = await fetch(
          `https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`
        );
        const itemTemp = await data.json();
        this.item = itemTemp;
        console.log(this.item);
      } catch (error) {
        console.log(error);
      }
    },
  },
  data() {
    return {
      item: [],
    };
  },
  created() {
    this.consumeApi();
  },
};
</script>

<style>
</style>