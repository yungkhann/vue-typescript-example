<template>
    <div class="job-list">
        <p> Ordered by {{order}} </p>
        <transition-group name="list" tag="ul">
            <li v-for="job in orderedJobs" :key = "job.id">
                <h2>
                    {{job.title}} in {{job.location}} 
                </h2>
                <div class="salary">
                    <p>Salary: {{job.salary}}</p>
                    <img src="../assets/kazakhstani-tenge.svg"   alt="">
                </div>
                <div class="description">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Itaque incidunt, sequi, animi architecto repellendus reprehenderit, natus inventore qui sed laboriosam exercitationem adipisci possimus! Iure, voluptatem et. Modi aspernatur sint quo?
                </div>
            </li>
        </transition-group>
    </div>
</template>

<script lang="ts">
import { computed, defineComponent, PropType } from 'vue'
import Job from '@/types/Job'
import OrderTerm from '@/types/OrderTerm'

export default defineComponent({
    props:{
        jobs:{
            type: Array as PropType<Job[]>,
            required:true
        },
        order:{
            type:String as PropType<OrderTerm>,
            required: true
        }
    },
    setup(props){
        const orderedJobs = computed(()=>{
            return [...props.jobs].sort((a:Job,b:Job)=>{
                return a[props.order] > b[props.order] ? 1 : -1
            })
        })

        return {orderedJobs}
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
        width: 10px;
        
    }
    .salary p {
        color: #17bf66;
        font-weight: bold;
        margin: 10px 4px;
    }
    .list-move{
        transition:all 0.4s
    }
</style>
