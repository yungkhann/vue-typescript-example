<template>
  <header>
    <div class="title">
      <h1>Nur Jobs</h1>
    </div>
    <div class="order">
      <button @click="handleClick('title')">order by title</button>
      <button @click="handleClick('location')">order by location</button>
      <button @click="handleClick('salary')">order by salary</button>
    </div>
  </header>
  <div class="app">  
    <JobList :jobs = "jobs" :order = "order"></JobList>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from 'vue';
import Job from './types/Job'
import JobList  from './components/JobList.vue'
import OrderTerm from './types/OrderTerm'
export default defineComponent({
  name: 'App',
  components: {
    JobList
  },
  setup(){
    const jobs = ref<Job[]>([
      {title:'Farm Worker', location:'Nursultan', salary:20000, id:'1'},
      {title:' Worker', location:'Almaty', salary:22000, id:'2'},
      {title:'Teacher', location:'Oskemen', salary:30000, id:'3'},
      {title:'Cooker', location:'Karaganda', salary:250000, id:'4'},
      {title:'Farm Worker', location:'Semey', salary:224000, id:'5'},

    ])

    const order = ref<OrderTerm>('title')
    const handleClick = (term:OrderTerm) =>{
      order.value = term
    }
    return {
      jobs, handleClick, order
    }
  },

  methods:{

  }
  
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
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
