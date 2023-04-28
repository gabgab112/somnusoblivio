<template>
  <v-dialog v-model="dialog1" width="auto">
    <v-card color="white" rounded="0" >
      <v-card-text class="text-h4 ">Bonjour, Charlotte!</v-card-text>
      <v-card-text class="text-h6 ">Voici les dernières actualités de ton compte:</v-card-text>
      <v-img src="../assets/BilletsVertical.png" width="5000px"/>
    </v-card>
    
    
  </v-dialog>

  <v-card color="teal-darken-3" class="pa-4" rounded="0">
    <v-card-text class="text-h4 ">Ton Compte</v-card-text>
    <v-form v-model="form" @submit.prevent="onSubmit">

      <v-text-field disabled label="Nom d'utilisateur: @charloYellowBanana"
        placeholder="Entrez votre mot de passe"></v-text-field>

      <v-text-field v-model="password" :readonly="loading" :rules="[required]" clearable label="Mot de passe"
        :type="show1 ? 'text' : 'password'" placeholder="Entrez votre mot de passe"></v-text-field>

      <v-btn :disabled="!form" :loading="loading" block color="teal-darken-4" rounded="0" size="large" type="submit"
        variant="elevated">
        Se Connecter
      </v-btn>
    </v-form>
  </v-card>
  <v-img src="../assets/Site.png" />



  <v-dialog v-model="dialog" width="auto">
    <v-card>
      <v-card-text>
        Mot de passe incorrect.
      </v-card-text>
      <v-card-actions>
        <v-btn color="teal-darken-4" block @click="dialog = false">Fermer</v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>

  
</template>

<script>

export default {
  name: 'HelloWorld',

  data: () => ({
    form: false,
    show1: false,
    password: "",
    confirmPassword: "09102022",
    loading: false,

    dialog: false,
    dialog1: false,
  }),
  methods: {
    onSubmit() {
      if (!this.form) return



      if (this.password === "09102022") {
        this.loading = true;
        this.dialog1 = true;

        setTimeout(() => (this.loading = false), 1000)
      }
      else {
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
<style>
body {
  background-color: #151515;
  font-family: 'Montserrat', sans-serif;
}
</style>
