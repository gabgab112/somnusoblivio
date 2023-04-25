<template>
<v-card class="mx-auto px-6 py-8 elevation-0" max-width="90%">
<h3>#UnComaPourManquerLesCours</h3>
    <h1>Apprends LE SORT qui fait fureur partout dans le Chemin de Traverse.</h1>
<br>
  <v-card color="teal-darken-3">
    <h1>Ton Compte</h1>
    <v-form v-model="form" @submit.prevent="onSubmit">

      <v-text-field v-model="password" :readonly="loading" :rules="[required]" clearable label="Mot de passe"
        :type="show1 ? 'text' : 'password'" placeholder="Entrez votre mot de passe"></v-text-field>

      <v-btn :disabled="!form" :loading="loading" block color="teal-darken-4" rounded="pill" size="large" type="submit" variant="elevated">
        Se Connecter
      </v-btn>
    </v-form>
  </v-card>

  <v-dialog
      v-model="dialog"
      width="auto"
    >
      <v-card>
        <v-card-text>
          Mot de passe incorrect.
        </v-card-text>
        <v-card-actions>
          <v-btn color="teal-darken-4" block @click="dialog = false">Fermer</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-card>
</template>

<script>

export default {
  name: 'HelloWorld',

  data: () => ({
    form: false,
    show1: false,
    password: "",
    confirmPassword: "test",
    loading: false,

    dialog: false,
  }),
  methods: {
    onSubmit() {
      if (!this.form) return

      

      if (this.password === "test") {
        this.loading = true;

        setTimeout(() => (this.loading = false), 1000)
      }
      else{
        this.dialog = true;
      }



    },
    required(v) {
      return !!v || 'Field is required'
    },

  },
  computed: {
    passwordConfirmationRule() {
      return () =>
        this.password === this.confirmPassword || "Password must match";
    }
  }
}
</script>
