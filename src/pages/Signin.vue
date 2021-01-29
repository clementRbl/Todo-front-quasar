<template>

    <div class="container-form q-pa-md q-mt-xl" style="width: 30%;">
      <div>Se connecter</div>
    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
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

  .flex-form {
    display: flex;
    justify-content: center;
  }

  .input-form {
    width: 150%;
  }
</style>