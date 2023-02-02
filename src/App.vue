<template>

  <div class="container grid-lg my-2 py-2 text-dark">
    <div class="card">
    
      <div class="card-header">
        <div class="h4">
          Exibindo as Moedas
        </div>
      </div>
      
      <div class="card-body">
        <Tabela :quotes="quotes" />
      </div>
    
    </div>
  </div>

</template>

<script>

import Tabela from './components/Tabela.vue';
import api from '@/servidor/api.js';
import { onMounted, reactive, toRefs } from 'vue';


export default {
  name: 'App',
  components: {
    Tabela
  },

  // Expor dados da nossa Api
  setup(){
    const data = reactive ({ // dados reativos

      quotes: { },

    });

    onMounted( async() => {
      const response = await api.all();
      data.quotes = response.data;
    });

    return { ...toRefs(data) }
  }
}
</script>

<style>
.h4{
  text-align: center;
  margin-bottom: 10px;
}

.card {
  box-shadow: 4px 4px 12px black;
}
</style>
