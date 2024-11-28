<template>
  <div>
    <div>
      <form id="peca-form" @submit="updatePeca">
        <div class="input_container">
          <label for="nome">Nome:</label>
          <input type="text" id="nome" name="nome" v-model="nome" required/>
        </div>
        <div class="input_container">
          <label for="carro">Carro:</label>
          <input
            list="carros"
            id="carro"
            name="carro"
            v-model="carro"
            required/>
          <datalist id="carros" required>
            <option
              v-for="carro in carros"
              :key="carro.id"
              :value="carro.model">
              {{ carro.model }}
            </option>
          </datalist>
        </div>
        <div class="input_container">
          <label for="nome">Placa:</label>
          <input type="text" id="placa" name="placa" v-model="placa" required/>
        </div>
        <div class="input_container">
          <input type="submit" class="submit_btn" value="Editar_Peça"/>
        </div>
        
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "EditPeca",
  data() {
    return {
      id: this.$route.params.id,
      nome: "",
      carro: "",
      carros: null,
      placa: "",
      plcas: null,
      msg: null,
    };
  },
  methods: {
    async getModelos() {
      const req = await fetch("http://localhost:3000/pecas_cadastradas");
      const data = await req.json();

      this.carros = data.modelos;
    },
    async updatePeca() {
      const req = await fetch("http://localhost:3000/items/" + this.id, {
        method: "PUT",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          nome: this.nome,
          carro: this.carro,
          placa: this.placa,
        }),
      });

      const res = await req.json();

    },
  },
  mounted() {
    fetch("http://localhost:3000/items/" + this.id)
      .then((res) => res.json())
      .then((data) => {
        this.nome = data.nome;
        this.carro = data.carro;
        this.placa = data.placa;
      });
    this.getModelos();
  },
};
</script>

<style scoped>
#peca-form {
  max-width: 400px;
  margin: 0 auto;
  border: 2px solid;
  padding: 10px;
  box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.75);
  -webkit-box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.75);
  -moz-box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.75);
}
.input_container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

label {
  font-weight: bold;
  margin-bottom: 15px;
  padding: 5px 10px;
}

input {
  padding: 5px 10px;
  width: 300px;
}

.submit_btn {
  background-color: #eac74d;
  font-weight: bold;
  transition: 0.5s;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
}

.submit_btn:hover {
  color: #fff;
}
</style>
