<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('location')">Order by location</button>
        <button @click="handleClick('salary')">Order by salary</button>
      </div>
    </header>
   <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import JobList from './components/jobsList.vue'
import Job from './types/job'
import OrderTerm from './types/OrderTerm'

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      {title: 'Secretary', location: 'Bulawayo', salary: 250, id: '1'},
      {title: 'Accountant', location: 'Harare', salary: 300, id: '2'},
      {title: 'Web-Developer', location: 'Mutare', salary: 500, id: '3'},
      {title: 'Teacher', location: 'Harare', salary: 150, id: '4'},
      {title: 'Teacher', location: 'Mutare', salary: 200, id: '5'},
    ])

    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return {
      jobs,
      handleClick,
      order
    }
  },
});
</script>

<style>
header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    color: #17bf66;
    border: 3px solid #17bf66;
    background: #ddffed;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }
</style>