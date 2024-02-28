<template>
  <v-app>


    <v-main>
      <TaskView/>
    </v-main>
  </v-app>
</template>

<script>
import TaskView from './components/TaskView';

export default {
  name: 'App',

  components: {
    TaskView,
  },

  data: () => ({
    //
  }),
};
</script>
