<script setup>
import { reactive } from 'vue';

const estado = reactive({
  numero1: 0,
  numero2: 0,
  filtro: 'todas',
}) 

function alteraNumero1(evento) {
  return estado.numero1 = Number(evento.target.value);
}

function alteraNumero2(evento) {
  return estado.numero2 = Number(evento.target.value);
}

const getResultadoSoma = () => {
  return estado.numero1 + estado.numero2;
}

const getResultadoSubtracao = () => {
  return estado.numero1 - estado.numero2;
}

const getResultadoDivisao = () => {
  return estado.numero1 / estado.numero2;
}

const getResultadoMultiplicacao = () => {
  return estado.numero1 * estado.numero2;
}

function alteraFiltro(evento) {
  return estado.filtro = evento.target.value;
}

const getCalculoFiiltrado = () => {
    const { filtro } = estado;

    switch (estado.filtro) {
      case 'soma':
      return getResultadoSoma();
      case 'subtracao':
      return getResultadoSubtracao();
      case 'divisao':
      return getResultadoDivisao();
      case 'multiplicacao':
      return getResultadoMultiplicacao();

  }
}

</script>

<template>
  <div class="container">
    <header class="p-6 mb-5 mt-5">
      <h1 class="mb-4">Calculadora Aritmética</h1>
      <form>
        <div class="row">
          <div class="col-md-3">
            <input type="number" placeholder="Digite o primeiro número" class="form-control" @change="alteraNumero1">
          </div>
          <div class="col-md-3">
            <input type="number" placeholder="Digite o segundo número" class="form-control" @change="alteraNumero2">
          </div>
          <div class="col-md-4">
            <select class="form-control" @change="alteraFiltro">
              {{ estado.numero1 }}
              {{ estado.numero2 }}
              <option>Escolha a função</option>
              <option value="soma">Somar</option>
              <option value="subtracao">Subtrair</option>
              <option value="divisao">Dividir</option>
              <option value="multiplicacao">Multiplicar</option>
            </select>
          </div>
        </div>
      </form>
      <p class="mt-4">
      O resultado foi: {{ getCalculoFiiltrado() }}
      </p>
    </header>
  </div>
</template>

<style scoped>

</style>
