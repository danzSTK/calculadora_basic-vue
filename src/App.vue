<script setup>
import { reactive } from 'vue';


const estado = reactive({
  valor1: 0,
  valor2: 0,
  resultado: 0,
  operador: '+',
})

const realizaOperacao = () =>{
  const valorLimpo1 = Number(estado.valor1)
  const valorLimpo2 = Number(estado.valor2)
  

  if(estado.operador === '/' && valorLimpo1 == 0 && valorLimpo2 == 0){
    return 0
  }

  switch(estado.operador){
    case '+': return valorLimpo1 + valorLimpo2
    case '-': return valorLimpo1 - valorLimpo2
    case 'x': return valorLimpo1 * valorLimpo2
    case '/': return valorLimpo1 / valorLimpo2
    default: return 'Erro type 001'
  }
}
</script>

<template>
  <div class="container">
    <header class="d-flex justify-content-center m-5">
      <h1 class="fw-bold">Calculadora Aritmética</h1>
    </header>

    <div class="display bg-dark  rounded-3 text-light">
      <header class="p-2 d-block">
        <h4 class="text-center text-uppercase">Resultado da operação:</h4>
      </header>
      <span class="d-block text-center fs-4 font-monospace ">{{ estado.valor1 }} {{ estado.operador }} {{estado.valor2}} = {{ realizaOperacao() }}</span>
    </div>

    <div class="row mt-5">
      <div class="col-md-5 col-lg-5 col-12">
        <label for="" class="form-label fw-semibold text-capitalize">Valor da operação</label>
        <input required @keyup="evento => estado.valor1 = evento.target.value" type="number" placeholder="Digite aqui o primeiro valor" class="form-control">
      </div>
      <div class="col-md-2 col-12">
        <label for="" class="form-label fw-semibold text-capitalize">Operador</label>
        <select @change="evento => estado.operador = evento.target.value" class="form-control text-center">
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="x">x</option>
          <option value="/">/</option>
        </select>
        {{ estado.operador }}
      </div>
      <div class="col-md-5 col-lg-5 col-12">
        <label  for="" class="form-label fw-semibold text-capitalize">Valor da operação</label>
        <input required @keyup="evento => estado.valor2 = evento.target.value" type="number" placeholder="Digite aqui o segundo valor" class="form-control">
      </div>
    </div>
  </div>

</template>

<style scoped>
  .display{
  
    margin: 0 auto;
    max-width: 600px;
    height: 120px;
  }

  input[type=number]::-webkit-outer-spin-button,
  input[type=number]::-webkit-inner-spin-button{
    -webkit-appearance: none;
  }
  
</style>
