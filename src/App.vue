<script setup>
import { reactive } from 'vue';


const estado = reactive({
  num1:'',
  num2:'', 
  operacao: '', 
  resultado:''
});

const calcular = () => {
  const num1 = parseFloat(estado.num1);
  const num2 = parseFloat(estado.num2);

  switch(estado.operacao) {
    case 'multiplicar':
      return num1*num2; 
    case 'dividir':
      return num1/num2; 
    case 'somar':
      return num1+num2; 
    case 'subtrair':
      return num1-num2; 
    default:
      return 'Insira um operador válido para operação!';
  }
}

</script>

<template>
<div class="container">
  <header class="mt-3">
    <h2>Calculadora Criada com Vue</h2>
  </header>
  <main>
    <div class="row mt-5">
      <div class="col-2">
        <input type="number" placeholder="Insira algum número" class="form-control text-center p-2" @input="evento => estado.num1 = evento.target.value">
      </div>
      <div class="col-4">
        <select class="form-control" @change="evento => estado.operacao = evento.target.value">
          <option value="selecione">selecione</option>
          <option value="multiplicar">multiplicar</option>
          <option value="dividir">dividir</option>
          <option value="somar">somar</option>
          <option value="subtrair">subtrair</option>
        </select>
      </div>
      <div class="col-2">
        <input type="number" placeholder="Insira algum número" class="form-control text-center p-2" @input="evento => estado.num2 = evento.target.value">
      </div>
    </div>
    <div class=" mt-4">
      <h4 class="mb-4 mt-5">Resultado da operação: </h4>
      <div class="resultado"  v-if="estado.num1 != '' && estado.num2 != ''">
        {{ calcular() }}
      </div>
      
    </div>
  </main>
</div>
</template>

<style scoped>
.resultado {
  font-size: 20px;  
}
</style>
