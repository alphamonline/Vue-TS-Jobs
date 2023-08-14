<template>
  <div class="app">
   vue-ts jobs
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from './types/job'

export default defineComponent({
  name: 'App',
  components: {},
  setup() {
    const jobs = ref<Job[]>([
      {title: 'Secretary', location: 'Bulawayo', salary: 250, id: '1'},
      {title: 'Accountant', location: 'Harare', salary: 300, id: '2'},
      {title: 'Web-Developer', location: 'Mutare', salary: 500, id: '3'},
      {title: 'Teacher', location: 'Harare', salary: 150, id: '4'},
      {title: 'Teacher', location: 'Mutare', salary: 200, id: '5'},
    ])

    return {
      jobs
    }
  },
});
</script>

<style>

</style>
