<script>
import axios from "axios";
export default {
  data() {
    return {
      novo_time: "",
      times: [],
    };
  },
  async created() {
    const times = await axios.get("http://localhost:4000/times");
    this.times = times.data;
  },
  methods: {
    async salvar() {
      const time = {
        nome: this.novo_time,
      };
      const time_criado = await axios.post("http://localhost:4000/times", time);
      this.times.push(time_criado.data);
      this.novo_time = "";
    },
    async excluir(time) {
      await axios.delete(`http://localhost:4000/times/${time.id}`);
      const indice = this.times.indexOf(time);
      this.times.splice(indice, 1);
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Gerencimento de Times</h2>
    </div>
    <div class="form-input">
      <input
        type="text"
        v-model="novo_time"
        @keyup.enter="salvar"
        placeholder="Times"
      />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-items">
      <table>
        <thead>
          <tr>
            <td>ID</td>
            <td>Nomes</td>
            <td>Ações</td>
          </tr>
        </thead>
        <tbody>
          <tr v-for="time in times" :key="time.id">
            <td>{{ time.id }}</td>
            <td>{{ time.nome }}</td>
            <td>
              <button>Editar</button>
              <button @click="excluir(time)">Apagar</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<style></style>
