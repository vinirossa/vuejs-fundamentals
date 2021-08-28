<template>
  <div :class="{'cliente': !isPremium,'cliente-premium': isPremium}">
    <h1>{{ cliente.nome }}</h1>
    <p>Email: {{ cliente.email }}</p>
    <p>Número: {{ numero }}</p>
    <p v-if="mostrarIdade">Idade: {{ cliente.idade }}</p>
    <p v-else>O usuário escondeu a idade</p>
    <!-- <p v-show="mostrarIdade">Idade: {{ cliente.idade }}</p> Não destrói o elemento -->
    <button @click="mudarCor($event)">Upgrade</button>
  </div>
</template>

<script>
  export default {
    data(){
      return {
        numero: "(19) 98562-6523"
      }
    },
    props: {
      cliente: Object,
      mostrarIdade: Boolean,
      isPremium: Boolean
    },
    methods: {
      mudarCor: function($event) {
        console.log($event)
        this.isPremium = !this.isPremium
      }
    }
  };
</script>

<style scoped>
.cliente {
  background-color: #ece5e3;
  height: 180px;
  max-width: 600px;
  border: gray solid 1px;
  padding-left: 20px;
  margin-top: 30px;
}
.cliente-premium {
  color: yellow;
  background-color: rgb(41, 41, 41);
  height: 180px;
  max-width: 600px;
  border: gray solid 1px;
  padding-left: 20px;
  margin-top: 30px;
}
</style>
