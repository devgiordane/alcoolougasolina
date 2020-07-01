<template>
  <div class="calc">
    <div class="logo">
      <img src="../assets/logo.png" alt="" />
    </div>
    <div class="inputs">
      <div class="input-group">
        <label for="">Gasolina</label>
        <div class="input-tag">
          <span>R$</span>
          <input v-model.number="gasolina" type="number" />
        </div>
      </div>
      <div class="input-group">
        <label for="">Álcool</label>
        <div class="input-tag">
          <span>R$</span>
          <input v-model.number="alcool" type="number" />
        </div>
      </div>
    </div>
    <div
      v-show="isFinite(resultado.porcetagem) && resultado.porcetagem > 0"
      class="resultado"
      :class="resultado.escolha"
    >
      <span>{{ resultado.mensagem }}</span>
    </div>
    <div class="medidor">
      <meter
        min="0"
        max="100"
        high="70"
        optimum="50"
        :value="resultado.porcetagem"
      >
      </meter>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculadora",
  data: function() {
    return {
      alcool: 3.01,
      gasolina: 4.46,
    };
  },
  computed: {
    resultado: function() {
      let porcetagem = ((this.alcool / this.gasolina) * 100).toFixed(0);
      let mensagem = porcetagem;
      let escolha = "";
      if (porcetagem > 70) {
        escolha = "gasolina";
        mensagem = `Com o álcool sendo ${porcetagem}% do valor da gasolina, é melhor abastecer com gasolina`;
      } else {
        escolha = "alcool";
        mensagem = `Com o álcool sendo ${porcetagem}% do valor da gasolina,é melhor abastecer com Álcool`;
      }

      return { mensagem, porcetagem, escolha };
    },
  },
};
</script>

<style lang="scss" scoped>
.logo {
  padding: 10px;
  text-align: center;
  img {
    width: 200px;
    height: auto;
  }
}
.inputs {
  padding: 10px;
  .input-group {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-bottom: 20px;
    label {
      font-size: 30px;
    }
    input {
      text-align: center;
      font-size: 40px;
      outline: none;
      border: none;
      border-bottom: 1px solid black;
      width: 50%;
    }
    .input-tag {
      display: flex;
      justify-content: center;
      align-items: baseline;
      span {
        font-weight: 900;
        color: #383838;
        font-size: 22px;
      }
    }
    input:focus {
      border-bottom: 2px solid #383838;
    }

    input::-webkit-outer-spin-button,
    input::-webkit-inner-spin-button {
      -webkit-appearance: none;
      margin: 0;
    }

    /* Firefox */
    input[type="number"] {
      -moz-appearance: textfield;
    }
  }
}
.resultado {
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
  font-size: 20px;
  text-align: center;
  &.alcool {
    background: green;
    color: white;
  }
  &.gasolina {
    background: orange;
  }
}
.medidor {
  display: flex;
  justify-content: center;
  meter {
    height: 50px;
    border-radius: none;
    width: 60vw;
  }
}
</style>
