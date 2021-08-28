<template>
  <div id="app">
    <h1>Guia Clientes</h1> <hr>
    <h2>Novo cliente</h2>
    <input type="text" placeholder="nome" v-model="nomeField"> <br>
    <small id="nome-erro" v-show="nomeInvalido">O nome não pode estar em branco.</small> <br>
    <input type="text" placeholder="email" v-model="emailField"> <br> <br>
    <input type="text" placeholder="idade" v-model="idadeField"> <br> <br>
    <button @click="cadastrarUsuario">Cadastrar</button>
    <br> <hr>
    <h2>Lista de clientes</h2>
    <div v-for="cliente in clientes" :key="cliente.id">
      <Cliente :cliente="cliente"/>
      <h4>Edição</h4>
      <input type="text" v-model="cliente.nome">
      <input type="text" v-model="cliente.email">
      <hr>
    </div>
  </div>
</template>

<script>
  import Cliente from "./components/Cliente.vue"
  // import Produto from "./components/Produto.vue"

  export default {
    name: "App",
    data(){
      return {
        clientes: [{
          nome: "Vinícius Pereira",
          email: "viniciuspsb@gmail.com",
          idade: 19,
          mostrarIdade: true
        },
        {
          nome: "Bianca Lima",
          email: "bianca@gmail.com",
          idade: 20,
          isPremium: true
        },
        {
          nome: "Maycon Diniz",
          email: "maycon@gmail.com",
          idade: 22,
          mostrarIdade: true
        },
        {
          nome: "João Silva",
          email: "joão@gmail.com",
          idade: 34,
        },
      ],
      }
    },
    components: {
      Cliente,
      // Produto,
    },
    methods: {
      cadastrarUsuario: function() {

        if(this.nomeField == "" || this.nomeField == " ") {
          this.nomeInvalido = true
        }

        this.clientes.push({id: Date.now(), nome: this.nomeField, email: this.emailField, idade: this.idadeField})
        this.nomeField = ""
        this.emailField = ""
        this.idadeField = ""    
        this.nomeInvalido = false
  
      }
    }
  };
</script>

<style>
#nome-erro {
  color: red;
}
</style>
