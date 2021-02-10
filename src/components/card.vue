<template>
  <v-row>
    <v-col cols="4" v-for="(dado, index) in dados" :key="index">
      <v-card>
        <v-card-title
          ><span style="color: black; font-size: 30px">
            {{ dado.name }}
          </span></v-card-title
        >
        <v-card-text> {{ dado.message }}</v-card-text>

        <!-- <v-btn
          color="blue"
          class="ml-4 mr-2 mb-2"
          outlined
          @click="atualizar(dado.id, dado dado.message)"
        ><v-icon>mdi-pencil</v-icon> 
        </v-btn> -->
        <v-btn
          text
          @click="
            {
              (dialog = true), (id = dado.id);
            }
          "
          color="blue"
          class="ml-4 mr-2 mb-2"
          outlined
        >
          <v-icon>mdi-pencil</v-icon>
        </v-btn>
        <v-btn color="red" class="mb-2" outlined @click="excluir(dado.id)">
          <v-icon> mdi-delete </v-icon>
        </v-btn>
      </v-card>
    </v-col>

    <v-dialog v-model="dialog" persistent max-width="600px">
      <v-card>
        <v-card-title>
          <span class="headline">Editar</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col cols="12">
                <v-textarea
                  v-model="message"
                  label="Message"
                  type="password"
                  required
                ></v-textarea>
              </v-col>
              <v-col cols="12" sm="6"> </v-col>
            </v-row>
          </v-container>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            text
            @click="dialog = false"
            color="red"
            class="ml-4 mr-2 mb-2"
            outlined
          >
            FECHAR
          </v-btn>

          <v-btn
            color="blue"
            class="ml-4 mr-2 mb-2"
            outlined
            @click="atualizar(id, message)"
          >
            Editar
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script>
export default {
  name: "Card",
  props: {
    dados: {
      default: () => {},
    },
  },
  data: () => ({
    id: "",
    message: "",
    dialog: false,
  }),

  methods: {
    excluir(id) {
      this.$emit("apagarMessage", id);
    },

    atualizar(id, message) {
      this.$emit("atualizarMessage", { id, message });
    },
  },
};
</script>

<style>
</style>