<script setup>
import { reactive, watch } from 'vue';

const estado = reactive({
  primeiroInput: '',
  segundoInput: '',
  operacao: '',
  resultado: ''
});

const calcularResultado = () => {
  const { primeiroInput, segundoInput, operacao } = estado;
  
  switch (operacao) {
    case 'adicao':
      estado.resultado = primeiroInput + segundoInput;
      break;
    case 'subtracao':
      estado.resultado = primeiroInput - segundoInput;
      break;
    case 'multiplicacao':
      estado.resultado = primeiroInput * segundoInput;
      break;
    case 'divisao':
      estado.resultado = primeiroInput / segundoInput;
      break;
    default:
      estado.resultado = 0;
  }
};

watch([() => estado.primeiroInput, () => estado.segundoInput, () => estado.operacao], calcularResultado);

</script>

<template>
  <div class="body">
    <div class="container">
      <main>
        <form>
          <h1>CALCULADORA ONLINE</h1>
          <div class="operadores">
            <input class="Primeiro__Input" placeholder="Digite um valor" type="number" v-model="estado.primeiroInput">
            <input class="Segundo__Input" placeholder="Digite um valor" type="number" v-model="estado.segundoInput">
          </div>
          <div class="resolucao">
            <input class="resultado" placeholder="Resultado" type="number" v-model="estado.resultado" readonly>
          </div>
          <select v-model="estado.operacao">
              <option value="">Escolha uma operação</option>
              <option value="adicao">Adição</option>
              <option value="subtracao">Subtração</option>
              <option value="multiplicacao">Multiplicação</option>
              <option value="divisao">Divisão</option>
          </select>
        </form>
      </main>
    </div>
  </div>
</template>

<style scoped>
.body {
  height: 80vh;
  width: 70vw;
}

.container {
  text-align: center;
  margin: 200px auto;
}

h1 {
  margin-bottom: 80px;
}

.operadores input, select {
  height: 30px;
  width: 170px;
  margin: 10px 5px;
}
.resolucao input {
  height: 30px;
  width: 170px;
  margin: 20px 5px;
}
</style>