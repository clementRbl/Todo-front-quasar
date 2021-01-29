<template>

    <div class="q-pa-md q-mt-xl">
      <div class="title-page">
        <h3>Connexion</h3>
      </div>
    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="form q-gutter-md"
    >
      <q-input
        filled
        v-model="email"
        class="input-form"
        type="email"
        label="Email *"
        lazy-rules
        clearable
        :rules="[ val => val && val.length > 0 || 'Le champ ne doit pas être vide']"
      />

      <q-input
        filled
        type="password"
        v-model="pwd"
        class="input-form"
        label="Mot de passe *"
        lazy-rules
        clearable
        :rules="[ val => val && val.length > 0 || 'Le champ ne doit pas être vide']"
      />

      <div>
        <q-btn label="Se connecter" type="submit" color="primary"/>
        <q-btn label="Pas de compte ?" to="/signup" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>
    </div>
</template>

<script>
export default {
  data () {
    return {
      email: null,
      pwd: null,

      accept: false
    }
  },

  methods: {
    onSubmit () {
      if (this.accept !== true) {
        this.$q.notify({
          color: 'red-5',
          textColor: 'white',
          icon: 'warning',
          message: 'You need to accept the license and terms first'
        })
      }
      else {
        this.$q.notify({
          color: 'green-4',
          textColor: 'white',
          icon: 'cloud_done',
          message: 'Submitted'
        })
      }
    },

    onReset () {
      this.email = null
      this.pwd = null
      this.accept = false
    }
  }
}
</script>

<style lang="scss">
  
   .form {
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .input-form {
    width: 50%;
  }

  .title-page {
    display: flex;
    justify-content: center;
  }

</style>