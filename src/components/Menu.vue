<template>
  <div class="">
    <div v-show="show" class="popup">
      <div class="header">
        <h4>{{ titulo }}</h4>
        <span @click="show = false">X</span>
      </div>
      <div v-html="conteudo" class=""></div>
    </div>
    <div class="menu">
      <div class="item">
        <span @click="(show = true), (titulo = 'SOBRE'), (conteudo = sobre)"
          >SOBRE</span
        >
      </div>
      <div class="item">
        <span
          @click="
            (show = true), (titulo = 'CONHEÇA OUTROS APPS'), (conteudo = apps)
          "
          >APPS</span
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Menu",
  data: function() {
    return {
      show: false,
      conteudo: "",
      titulo: "",
      sobre: `
        <p>Como funciona o aplicativo álcool ou gasolina</p>

        <p>
        O aplicativo calcula a média de preço entre os combustíveis, e retorna um
        resultado baseado na percentual de diferença do álcool entre gasolina, se o
        valor do álcool for até 70% do valor da gasolina será mais vantajoso abastecer
        como álcool ou se não, com gasolina.
        </p>

      `,
      apps: `
        <ul class="lista">
        <li><a href="#">Gerador de link para whatsApp</a></li>
        <li><a href="#">Quiz sobre jogos</a></li>
        <li><a href="#">Calculadora de IMC</a></li>
        <li><a href="#">Tabuada das 4 operações</a></li>
        </ul>
      `,
    };
  },
};
</script>

<style lang="scss">
.menu {
  background: green;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-right: 20px;
  padding-left: 20px;
  height: 40px;
  .item {
    cursor: pointer;
    padding: 0px 10px;
    &:hover {
      border: 1px solid white;
    }
  }
}
@media (min-width: 1020px) {
  .menu {
    justify-content: space-around;
  }
}
.popup {
  background: #006100;
  color: white;
  padding: 0px 20px;
  padding-bottom: 20px;
  margin: 0px 20px;
  border-radius: 20px 20px 0px 0px;
  -webkit-box-shadow: 3px 0px 17px 5px rgba(0, 0, 0, 0.45);
  -moz-box-shadow: 3px 0px 17px 5px rgba(0, 0, 0, 0.45);
  box-shadow: 3px 0px 17px 5px rgba(0, 0, 0, 0.45);

  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-top: 0px;
    span {
      cursor: pointer;
      padding: 5px;
      &:hover {
        background: rgba(0, 0, 0, 0.411);
        color: red;
      }
    }
  }
  .lista {
    list-style: none;
    li {
      padding-left: 5px;
      &:hover {
        background: white;
        border-left: 30px solid #006100;
        a {
          color: green;
        }
      }
      a {
        color: white;
        text-decoration: none;
      }
    }
  }
}
</style>
