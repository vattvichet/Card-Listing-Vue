<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">Sort By Title</button>
        <button @click="handleClick('salary')">Sort By Salary</button>
        <button @click="handleClick('location')">Sort By Location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import type { Job } from './types/job'
import JobList from './components/job_list.vue'
import type { OrderTerm } from './types/orderTerm'

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      { title: 'Seller', location: 'Phnom Penh🏢', salary: 500, id: 1 },
      { title: 'Developer', location: 'Phnom Penh🏢', salary: 1500, id: 2 },
      { title: 'Teacher', location: 'Phnom Penh🏢', salary: 750, id: 3 }
    ])

    const order = ref<OrderTerm>('title')
    const handleClick = (term: OrderTerm) => {
      order.value = term
    }
    return { jobs, handleClick, order }
  },
  methods: {}
})
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
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
