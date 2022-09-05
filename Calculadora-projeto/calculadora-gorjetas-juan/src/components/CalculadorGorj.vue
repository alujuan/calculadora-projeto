<script>
export default {
  data() {
    return {
      serviceQuality: [
        { quality: 5, service: "5%(péssimo)" },
        { quality: 10, service: "10%(ruim)" },
        { quality: 15, service: "15%(ok)" },
        { quality: 20, service: "20%(bom)" },
        { quality: 25, service: "25%(mais que bom)" },
        { quality: 30, service: "30%(excepcional)" },
      ],
      value: 0,
      qntdPessoa: 1,
      selected_quality: "",
    };
  },
  computed: {
    final_value() {
      return (
        (this.value * (1 + this.selected_quality / 100)) /
        this.qntdPessoa
      ).toFixed(2);
    },
  },
};
</script>

<template>
  <main>
    <div id="header">
      <h1>Calculadora de Gorjeta</h1>
      <div class="value-select">
        <label for="input-value">Valor do serviço?</label>
        <input id="input-value" type="number" placeholder="0" v-model="value" />
      </div>
      <div class="value-select">
        <label for="select-service">Qualidade do serviço:</label>
        <select
          v-model="selected_quality"
          name="select-quality"
          id="select-service"
        >
          <option disabled value="">percentual da gorjeta</option>
          <option
            v-for="quality of serviceQuality"
            :key="quality.quality"
            for="select-service"
            :value="quality.quality"
          >
            {{ quality.service }}
          </option>
        </select>
      </div>
      <div class="value-select">
        <label for="input-pessoas"
          >Quantidade de pessoas pagando a conta:</label
        >
        <input
          v-model="qntdPessoa"
          placeholder="1"
          id="input-pessoas"
          type="number"
        />
      </div>
      <div class="result">
        <h2>Valor da conta:</h2>
        <span>R$ {{ final_value }} por pessoa</span>
      </div>
    </div>
  </main>
</template>

<style></style>
