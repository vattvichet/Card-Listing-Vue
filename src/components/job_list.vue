<template>
  <div class="job-list">
    <p>Order by {{ order }}</p>
    <ul>
      <li v-for="job in orderedJobs" :key="job.id">
        <div class="jobCard">
          <h2>{{ job.title }} In {{ job.location }}</h2>
          <div class="salary">
            <p>{{ job.salary }} $</p>
          </div>
          <div class="description">
            <p>
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Porro quam adipisci earum
              deleniti vitae ea saepe, ad quia sint assumenda ratione nam eaque veritatis pariatur
              quisquam odit tempore, repellendus cumque!
            </p>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue'
import type { PropType } from 'vue'
import type { Job } from './../types/job'
import type { OrderTerm } from './../types/orderTerm'

export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>
    }
  },

  setup(props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1
      })
    })
    return { orderedJobs }
  }
})
</script>

<style scoped>
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
.job-list ul {
  padding: 0;
}
.job-list li {
  list-style-type: none;
  background: white;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
}
.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
}
.salary img {
  width: 30px;
}
.salary p {
  color: #17bf66;
  font-weight: bold;
  margin: 10px 4px;
}

.jobCard {
  border-radius: 25px;
  padding: 20px; /* Adjust the padding value according to your preference */
  border: 1px solid #ccc; /* Optional: Add a border for better visibility */
}

.jobCard h2 {
  margin-bottom: 10px;
}

.salary {
  margin-bottom: 10px;
}

.description {
  color: #555; /* Optional: Adjust the text color */
}
</style>
