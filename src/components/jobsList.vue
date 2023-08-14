<template>
    <div class="job-list">
        <p>Ordered by {{ order }}</p>
        <ul>
            <li v-for="job in orderedJobs" :key="job.id">
                <h2>{{ job.title }} in {{ job.location }}</h2>
                <div class="salary">
                    <p>$ {{ job.salary }}</p>
                </div>
                <div class="description">
                    <p>
                        Lorem ipsum dolor sit amet consectetur adipisicing elit. Quos aliquam 
                        iure atque odio voluptatum quaerat delectus ipsum repellendus doloremque 
                        sapiente illum natus, doloribus animi et aperiam saepe, ullam deleniti assumenda.
                    </p>
                </div>
            </li>
        </ul>
    </div>
</template>

<script lang="ts">
import { computed, defineComponent, PropType } from 'vue'
import Job from '@/types/job'
import OrderTerm from '@/types/OrderTerm'

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
                /* Here we will sort based on orderTerm 
                 * Compare ther order property of 'a' the first job to the order property of 'b'
                 * If 'a' is bigger than 'b' we want to return 1 which means true. Thus, this sort((a: Job, b: Job) switch places
                 * If 'a' is smaller than 'b' we want to return -1 which means false. Thus, this sort((a: Job, b: Job) will not switch places
                 * return computed value
                */
                return a[props.order] > b[props.order] ? 1 : -1
            })
        })

        return {
            orderedJobs
        }
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
</style>
@/types/job