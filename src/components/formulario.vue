<template>
  <v-row class="d-flex">
    <v-col cols="12">
      <v-card class="pa-5" min-width="300px">
        <v-form ref="form" lazy-validation v-on:atualizarMessage="atualizar">
          <v-text-field
            v-model="name"
            :counter="10"
            :rules="[(v) => !!v || 'E-mail is required']"
            label="Usuário"
            required
            ma="2"
          ></v-text-field>
          <v-textarea
            v-model="message"
            filled
            auto-grow
            label="Mensagem"
            rows="4"
            row-height="30"
            shaped
          ></v-textarea>
          <v-btn color="success" class="mr-4" @click="enviar"> Enviar </v-btn>
        </v-form>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "Formulario",
  data: () => ({
    name: "",
    message: "",
  }),

  props: {
    id: {
      type: String,
      default: "",
    },
  },

  methods: {
    enviar() {
      this.$emit("criarMessage", { name: this.name, message: this.message });
    },
  },
};
</script>

<style>
</style>