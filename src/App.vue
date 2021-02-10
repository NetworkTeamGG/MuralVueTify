<template>
  <v-app>
    <v-main class="grey lighten-3" min-width="840px">
      <v-container>
        <Header />
        <Formulario :name="user" :message="message" @criarMessage="enviar" />
        <Card
          :dados="dados"
          @apagarMessage="excluir"
          @atualizarMessage="atualizar"
        />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import axios from "axios";
import Header from "./components/navbar.vue";
import Formulario from "./components/formulario.vue";
import Card from "./components/card.vue";

export default {
  name: "App",

  data: () => ({
    dados: [],
    id: "",
    user: "",
    message: "",
  }),

  components: {
    Header,
    Formulario,
    Card,
  },

  created() {
    this.buscar();
  },

  methods: {
    atualizar({ id, message }) {
      console.log(id, message);
      axios
        .create({
          baseURL: "http://100.64.144.209:3000/",
          timeout: 10000,
        })
        .put("/mural", { id, message })
        .then((response) => {
          console.log(response.data);
          this.buscar();
        })
        .catch((error) => {
          alert(error);
        });
    },
    enviar({ name, message }) {
      axios
        .create({
          baseURL: "http://100.64.144.209:3000/",
          timeout: 10000,
        })
        .post("/mural", { name, message })
        .then((response) => {
          console.log(response);
          this.buscar();
        })
        .catch((error) => {
          alert(error);
        });
    },

    buscar() {
      axios
        .create({
          baseURL: "http://100.64.144.209:3000/",
          timeout: 10000,
        })
        .get("/mural")
        .then((response) => {
          console.log(response.data.mural);
          this.dados = response.data.map((dados) => {
            console.log(dados);
            return {
              id: dados.id,
              name: dados.name,
              message: dados.message,
            };
          });
        })
        .catch((error) => {
          alert(error);
        });
    },
    excluir(id) {
      axios
        .create({
          baseURL: "http://100.64.144.209:3000/",
          timeout: 10000,
        })

        .delete(`/mural/${id}`)
        .then((response) => {
          console.log(response);
          this.buscar();
        })
        .catch((error) => {
          alert(error);
        });
    },
  },
};
</script>

<style scoped>
</style>
