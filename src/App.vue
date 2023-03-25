<script setup>
import { reactive } from 'vue';

const operacao = reactive({
  operadores: '',
  numeroA: 0,
  numeroB: 0,
})

const primeiroNumero = operacao.numeroA;
const segundoNumero = operacao.numeroB;

function somar () {
  return primeiroNumero + segundoNumero;
}

function subtrair () {
  return primeiroNumero - segundoNumero;
}

function dividir () {
  return primeiroNumero / segundoNumero;
}

function multiplicar () {
  return primeiroNumero * segundoNumero;
}


const getResultado = () => {
  const {operadores} = operacao;

  switch(operadores) {
    case '+':
      return somar();
    case '-':
      return subtrair();
    case '*':
      return multiplicar();
    case '/':
      return dividir();
  }
}
</script>

<template>
  <div class="container">
    <section class="">
      <div class="row d-flex justify-content-center ">
        <div class="col-md-8">
          <form class="">
        <div class="row d-flex justify-content-center">
          <div class="col-md-6 bg-light">
            <h1 class="text-center mt-2">Calculadora Aritmética</h1>
            <div class="d-flex align-items-center justify-content-center pt-3 pb-3">
              <input type="number" @keyup="evento => operacao.numeroA = evento.target.value" class="form-control me-2 w-50 ">
              <select class="form-control w-25" @change="evento => operacao.operadores = evento.target.value">
                  <option value="+">+</option>
                  <option value="-">-</option>
                  <option value="*">*</option>
                  <option value="/">/</option>
                </select>
                <input type="number" @keyup="evento => operacao.numeroB = evento.target.value" class="form-control ms-2 w-50">
            </div>
            <div class="row text-center">
              <span>O Resultado é</span>
              <span> {{ getResultado() }}</span>     
            </div>
          </div>
        </div>
          </form>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped></style>