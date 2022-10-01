<script>
import axios from "axios";
export default {
  data() {
    return{
      cep: "",
      endereco: {},
    };
  },
  methods: {
  async buscar() {
    const url = `https://viacep.com.br/ws/${this.cep}/json/`;
    const res = await axios.get(url);
    this.endereco = res.data;
   },
  },
};
</script>

<template>

  <main>

    <h1>Buscar Cep</h1>
    
    <form @submit.prevent="buscar">
      <input type="text" v-model ="cep" placeholder="Digite o CEP"/>
      <button type="submit">Buscar</button>
    </form>
    
    <form class="end">
      
      <label for="rua">Rua</label> <input type="text" v-model="endereco.logradouro" />
      <label for="num">Numero</label> <input type="text" v-model="endereco.numero" />
      <label for="bairro">Bairro</label> <input type="text" v-model="endereco.bairro" />
      
    </form>
    {{endereco}}
  </main>
    
  </template>

<style>
  body{
    background-color: aqua;
  }

h1{
  display: flex;
  justify-content: center;
  margin-bottom: 100px;
}

.end{
  display: flex;
  flex-direction: column;
  align-items: center;
}

.end input{
  padding-left: 10px;
  margin: 5px;
}

input{
  padding-left: 100px;
  margin-right: 5px;
}

form {
  margin-top: 50px;
  display: flex;
  justify-content: center;
  background-color: aquamarine;
}

main{
  margin-top: 100px;
  background-color: aquamarine;
  margin-left: 50px;
  margin-right: 50px;
  padding-bottom: 50px;
  border-radius: 25px;
  border: 2px solid black ;
}

</style>