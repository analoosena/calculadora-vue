<script setup>

  import { reactive } from 'vue';
  const estado = reactive ({
    number1: 0,
    number2: 0,
    filtro: '',
  })

  function calculaOperacao(){
    const filtro = estado.filtro;

    const num1 = parseFloat(estado.number1);
    const num2 = parseFloat(estado.number2);

    switch(filtro){
      case 'adicao':
        return num1 + num2;
      case 'subtracao':
        return num1 - num2;
      case 'multiplicacao':
        return num1 * num2;
      case 'divisao':
        return num1 / num2;
    }
  }

</script>

<template>
<div class="container bg-secondary-subtle p-5">
  <h2 class="text-center pb-4">➥ Calculadora Aritmética</h2>
  <div class="container-sm pt-4 ">
    <div class="row justify-content-center grid gap-3 ">
      <div class="col-4">
        <input @keyup="evento => estado.number1 = evento.target.value" class="form-control" type="number" placeholder="Digite o 1° n°">
      </div>
      <div class="col-2">
        <select @change="evento => estado.filtro = evento.target.value" class="btn btn-outline-secondary dropdown-toggle">
          <option value="">?</option>
          <option value="adicao"> + </option>
          <option value="subtracao"> - </option>
          <option value="multiplicacao">  x </option>
          <option value="divisao"> ÷ </option>
        </select>
      </div>
      <div class="col-4">
        <input @keyup="evento => estado.number2 = evento.target.value" class="form-control" type="number" placeholder="Digite o 2° n°">
      </div>
    </div>

    <div class="row justify-content-center pt-5">
      <div class="col-6 d-flex justify-content-center ">
        <span class="border border-info p-5 border-4 text center">
            <p v-if="estado.number1.length > 0 && estado.number2.length > 0"> {{ calculaOperacao() }}</p>
            <p v-else>?</p>
          </span>
        
      </div>
    </div>
  </div>
  
</div>
</template>

<style scoped>


</style>
