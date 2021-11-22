<template>
  <div>
    <Message :msg="msg" v-show="msg" />
    <div>
      <form id="burger_form" @submit="createBurger">
        <div class="input_container">
          <label for="nome">Nome do cliente</label>
          <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite seu nome" />
        </div>
        <div class="input_container">
          <label for="pao">Escolha o pão</label>
          <select id="pao" v-model="pao">
            <option value="">Selecione seu pão</option>
            <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{pao.tipo}}</option>
          </select>
        </div>
        <div class="input_container">
          <label for="carne">Escolha a carne do seu Burger</label>
          <select id="carne" v-model="carne">
            <option value="">Selecione o tipo de carne</option>
            <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{carne.tipo}}</option>
          </select>
        </div>
        <div class="input_container opcionais_container">
          <label for="opcionais" class="opcionais_title">Escolha seus opcionais</label>
          <div class="checkbox_container" v-for="opcional in opcionaisData" :key="opcional.id" >
            <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
            <span>{{opcional.tipo}}</span>
          </div>
        </div>
        <div class="input_container">
          <input type="submit" class="submit_btn" value="Criar meu burger" />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import Message from "@/components/Message";

export default {
  name: "BurgerForm",
  components: {Message},
  data () {
    return {
      paes: null,
      carnes: null,
      opcionaisData: null,
      nome: null,
      pao: null,
      carne: null,
      opcionais: [],
      msg: null,
    }
  },
  methods: {
    async recuperarIngredientes () {
      const req = await fetch('http://localhost:3000/ingredientes');
      const data = await req.json();

      this.paes = data.paes;
      this.carnes = data.carnes;
      this.opcionaisData = data.opcionais;
    },

    async createBurger(e) {
      e.preventDefault();

      const data = {
        nome: this.nome,
        carne: this.carne,
        pao: this.pao,
        opcionais: Array.from(this.opcionais),
        status: "Solicitado"
      }

      const dataJson = JSON.stringify(data);

      const req = await fetch("http://localhost:3000/burgers", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: dataJson
      });

      const res = await req.json();

      this.msg = `Pedido nº ${res.id} realizado com sucesso`

      setTimeout(() => {
        this.msg = ""
      }, [3000]);

      this.nome = "";
      this.carne = "";
      this.pao = "";
      this.opcionais = "";
    }
  },
  mounted() {
    this.recuperarIngredientes();
  }
}
</script>

<style scoped>
#burger_form {
  max-width: 400px;
  margin: 0 auto;
}

.input_container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

label {
  font-weight: bold;
  margin-bottom: 15px;
  color: #222;
  padding: 5px 10px;
  border-left: 4px solid #fcba03;
}

input, select {
  padding: 5px 10px;
  width: 300px;
}

.opcionais_container {
  flex-direction: row;
  flex-wrap: wrap;
}

.opcionais_title {
  width: 100%;
}

.checkbox_container {
  display: flex;
  align-items: flex-start;
  width: 50%;
  margin-bottom: 20px;
}

.checkbox_container span,
.checkbox_container input {
  width: auto
}

.checkbox_container span {
  margin-left: 6px;
  font-weight: bold;
}

.submit_btn {
  background-color: #222222;
  color: #fcba03;
  font-weight: bold;
  font-size: 16px;

  border: 2px solid #222;
  padding: 10px;
  margin: 0 auto;

  cursor: pointer;
  transition: .5s;
}

.submit_btn:hover {
  background-color: transparent;
  color: #222222;
}

</style>