<template>
  <q-layout view="lHh Lpr lFf" >
    <q-header elevated>
      <q-toolbar class="bg-black">
        <q-btn
          flat @click="drawer = !drawer" round dense icon="menu" />

          <div class="container-buttons">
              <div class=" buttons q-pa-md q-gutter-sm">
                <q-btn  to="/signin" outline style="color: white;"  label="Connexion" />
              </div>
              
          <div class=" buttons q-pa-md q-gutter-sm">
            <q-btn to="/signup" outline style="color: white;" label="Inscription" />
          </div>
        </div>

      </q-toolbar>

    </q-header>

   <q-drawer
        v-model="drawer"
        :width="250"
        :breakpoint="500"
        
      >
        <q-scroll-area class="fit">
          <q-list padding class="menu-list">

            <q-item to="/todo" clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="speaker_notes" />
              </q-item-section>

              <q-item-section>
                Créer une Todo List
              </q-item-section>
            </q-item>

            <q-item to="/signin" clickable v-ripple>
              <q-item-section avatar >
                <q-icon name="login" />
              </q-item-section>

              <q-item-section>
                Se connecter
              </q-item-section>
            </q-item>

            <q-item to="/signup" clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="account_box" />
              </q-item-section>

              <q-item-section>
                S'inscrire
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>
      </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<style lang="scss">
  .logo-technow {
    margin-left: 2%;
    width: 120px;
    height: 100px;
  }
  .container-buttons {
    display: flex;
    width: 100%;
    justify-content: flex-end;
  }
  .container-logo-slide{
    background-color: black;
  }
  .menu-list {
    display: flex;
    flex-direction: column;
  }
  .logo-drawer {
    margin-top: -17%;
  }
  
</style>

<script>
export default {
  name: 'MainLayout',
  data () {
    return {
      drawer: false
    }
  }
}
</script>