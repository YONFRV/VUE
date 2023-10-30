<script setup>
import {ref,onMounted} from 'vue';
import { useAuthStore } from '../../stores/auth';
import {Bar,Pie} from 'vue-chartjs';
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, 
    LinearScale, ArcElement } from 'chart.js';
import axios from 'axios';
ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale
,ArcElement);
const authStore = useAuthStore();
axios.defaults.headers.common['Authorization'] = 'Bearer '+authStore.authToken;

const departments = ref([]);
const employees = ref([]);
const chartData = ref([]);
const chartOptions = ref([]);
const colors = ref([]);
const loaded = ref(false);
const random = () =>{
    return Math.floor(Math.random() * 256);
}
onMounted( async () =>{
    const info = await axios.get('/api/employeesbydepartment');
    info.data.map((row)=>(
        departments.value.push(row.name),
        employees.value.push(row.count),
        colors.value.push("rgb("+random()+","+random()+","+random()+")")
    ));
    chartOptions.value= { responsive:true}
    chartData.value = {
        labels:departments.value,
        datasets:[
            {label:'Employees', data:employees.value, backgroundColor:colors}
        ]
    };
    loaded.value = true;
})
</script>
<template>
    <div class="row">
        <div class="col-md-8 offset-md-2">
            <Bar v-if="loaded" :data="chartData" :options="chartOptions"></Bar>
        </div>
    </div>
</template>