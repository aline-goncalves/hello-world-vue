<template>
  <main class="columns is-gapless is-multline" :class="{ 'dark-mode': isDarkModeActive }">
    <div class="column is-one-quarter">
      <lateral-bar @whenThemeChanged="changeTheme"></lateral-bar>
    </div>
    <div class="column is-three-quarter content">
      <form-task @whenTaskSaved="saveTask"></form-task>
      <div class="list">
        <task-component v-for="task, index in tasks" :key="index" :task="task"></task-component>
        <box-component v-if="isListEmpty">Não existem tarefas registradas hoje :/</box-component>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import FormTask from './components/FormTask.vue';
import LateralBar from './components/LateralBar.vue';
import TaskComponent from './components/TaskComponent.vue';
import TaskInterface from './interfaces/TaskInterface';
import BoxComponent from './components/BoxComponent.vue';

export default defineComponent({
  name: 'App',
  components: {
  LateralBar,
  FormTask,
  TaskComponent,
  BoxComponent
  },
  data (){
    return {
      tasks: [] as TaskInterface[],
      isDarkModeActive: false
    }
  },
  computed:{
    isListEmpty () : boolean{
      return this.tasks.length === 0
    }
  },
  methods:{
    saveTask(task:TaskInterface){
      this.tasks.push(task);
    },
    changeTheme(isDarkModeActive: boolean){
      this.isDarkModeActive = isDarkModeActive
    }
  }
});
</script>

<style>
.list{
  padding: 1.25rem;
}
main{
  --bg-primary: #fff;
  --text-primary: #000;
}
main.dark-mode{
  --bg-primary: #2b2d42;
  --text-primary: #ddd;
}
.content{
  background: var(--bg-primary);
}
</style>
