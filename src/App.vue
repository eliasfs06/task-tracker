<template>
  <main class="columns is-gapless is-multiline" :class="{ 'dark-mode' : isDarkModeOn }">
    <div class="column is-one-quarter">
      <SideBar @changeTema="changeTema" />
    </div>
    <div class="column is-three-quarter content">
      <AppForm @whenSaveTask="saveTask"/>
      <div class="list">
        <FormTask v-for="(task, index) in tasks" :key="index" :task="task"/>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SideBar from './components/SideBar.vue';
import AppForm from './components/AppForm.vue';
import FormTask from './components/FormTask.vue';
import ITasks from './interfaces/ITasks';

export default defineComponent({
  name: 'App',
  components: {
    SideBar,
    AppForm,
    FormTask
  },
  data () {
    return {
      tasks: [] as ITasks[],
      isDarkModeOn: false
    }
  },
  methods: {
    saveTask(task: ITasks){
      this.tasks.push(task)
    },
    changeTema (isDarkModeOn: boolean) {
      this.isDarkModeOn = isDarkModeOn
    }
  }
});
</script>

<style>
.list {
  padding: 1.25rem;
}
main {
  --bg-primario: #fff;
  --texto-primario: #000;
}
main.dark-mode {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}
.content{
  background-color: var(--bg-primario);
  color: var(--texto-primario);
}
</style>
