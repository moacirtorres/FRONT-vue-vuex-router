<template>
  
<section>
  <h1>Compre ou Venda</h1>
  <produtos-buscar/>
  <produtos-lista/>
</section>


</template>

<script>
// @ is an alias to /src

import ProdutosBuscar from '@/components/ProdutosBuscar.vue'
import ProdutosLista from '@/components/ProdutosLista.vue'



export default {
  name: 'Home',
  components: {ProdutosBuscar, ProdutosLista}
}
</script>

<style scoped>
  h1 {
    font-size: 2rem;
    color: #87f;
    margin-top: 40px;
    text-align: center;
  }
</style>
