<template>
<q-page class="bg-grey-3 column">
  <div class="row q-pa-sm bg-white">
     <q-input
      v-model="newTask" 
      @keyup.enter="addTask"
      class="col" 
      square 
      bg-color="white" 
      filled 
      placeholder="Ajouter une tache"
      dense
      >
      <template v-slot:append>
        <q-btn @click="addTask()" round dense flat icon="add" />
       </template>
    </q-input>
  
  </div>
  <div class="q-pa-md">
    <div class="q-gutter-sm">
    <q-list separator class="bg-white">

      <q-item
       v-for="(task, index) in tasks"
       :key="task.title"
       @click="task.done = !task.done"
       :class="{ 'done bg-blue-1' : task.done}"
       
       >
        
        <q-item-section avatar>
          <q-checkbox v-model="task.done" class="pointer-events: none;" color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{task.title}}</q-item-label>
        </q-item-section>
         <q-item-section v-if="task.done"
          side>
          <q-btn @click.stop="deleteTask(index)" flat round dense color="negative" icon="delete" />
        </q-item-section>
      </q-item>

    </q-list>
      <div 
      v-if="!tasks.length"
      class="no-tasks absolute-center">
        <div class="text-h5 text-primary text-center">Pas de taches</div>
      </div>


    </div>

  </div>
</q-page>
  
</template>

<script>
export default {
  data () {
    return {
      newTask: '',
      tasks: [
      /* {
        title: 'Acheter du pain',
        done: false,
        urgent: false
      },
      {
        title: 'Payer le dealer',
        done: false,
        urgent: false
      },
      {
        title: 'Faire un doigt à la police',
        done: false,
        urgent: false
      } */
      ]
    }
  },
  methods: {
    deleteTask(index) {
      this.$q.dialog({
        title: 'Suppression',
        message: 'Vous êtes sur de vouloir supprimer cette tache ?',
        cancel: true,
        persistent: true
      }).onOk(() => {
          this.tasks.splice(index ,1)
          this.$q.notify('Tache supprimé !')
      })
    },

    addTask() {
      this.tasks.push({
        title: this.newTask,
        done: false
      })
      this.newTask = ''
    }
  }
}
</script>

<style lang="scss">
   .item {
    background-color: red;
    pointer-events: none;
  }
  .done {
    .q-item__label {
      text-decoration: line-through;
      color: #bbb;
    }
  }
  .no-tasks {
    opacity: 0.5;

  }

</style>