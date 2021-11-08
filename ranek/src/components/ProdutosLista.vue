<template>
  <section class="produtos-container">
    <div v-for="produto in produtos" :key="produto.id">
        <p class="preco">{{ produto.preco }}</p>
      <h2 class="titulo">{{ produto.nome }}</h2>
      <img :src="produto.fotos[0]" :alt="produto.fotos[0]" />
      <p class="descricao">{{ produto.descricao }}</p>
    </div>
  </section>
</template>

<script>

import { api } from '@/services.js'
import { serialize } from '@/helpers.js'

export default {
  data() {
    return {
      produtos: null,
      produtosPorPagina: 9
    };
  },
  name: "produtos-lista",
  computed: {
      url() {
          const query = serialize(this.$route.query)
          return "/produto?_limit=${this.produtosPorPagina}" + query
      }
  },
  methods: {
    getProdutos() {
      api.get(this.url).then((r) => {
        this.produtos = r.data;
      });
    },
  },
  watch: {
      url() {
        this.getProdutos();
      }
  },
  created() {
    this.getProdutos();
  },
};
</script>

<style scoped>
</style>