<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar/>
    </div>
    <div class="column is-three-quarter">
      <FormToDo @whenSavingTask="saveTask"/>
      <div class="lista">
        <TaskToDo v-for="(task, index) in tasks" :key="index" :task="task"/>
        <BoxList v-if="emptyList">
          you don't have any tasks registered
        </BoxList>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SideBar from './components/SideBar.vue'
import FormToDo from './components/FormToDo.vue';
import TaskToDo from './components/TaskToDo.vue';
import ITask from './interfaces/ITask'
import BoxList from './components/BoxList.vue'


export default defineComponent({
  components: { 
    SideBar,
    FormToDo,
    TaskToDo, 
    BoxList
    },
  name: 'App',

  data (){
    return{
      tasks: [] as ITask[]
    }
  },

  computed: {
    emptyList() : boolean{
      return this.tasks.length === 0
    }
  },

  methods: {
    saveTask(task: ITask){
      this.tasks.push(task)
    }
  }
});
</script>

<style>
body{
  background: #2e2e2e;
}

.lista{
  padding: 1.25rem;
}

</style>
