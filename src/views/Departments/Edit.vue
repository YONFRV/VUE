<script setup>
import {ref,onMounted} from 'vue';
import { useRoute } from 'vue-router';
import { sendRequest } from '../../functions';
import { useAuthStore } from '../../stores/auth';
import { useRouter } from 'vue-router';
import axios from 'axios';
const route = useRoute();
const authStore = useAuthStore();
axios.defaults.headers.common['Authorization'] = 'Bearer '+authStore.authToken;
const form = ref({ id:'', name:'' });
const id = ref(route.params.id);
onMounted( () => { getDepartment()});
const getDepartment = () =>{
    axios.get('api/departments/'+id.value).then(
        response => (form.value.name = response.data.data.name)
    );
}
const save = () =>{
    sendRequest('PUT',form.value,('/api/departments/'+id.value),'/departments');
}
</script>
<template>
    <div class="row mt-5">
        <div class="col-md-4 offset-md-4">
            <div class="card border border-success">
                <div class="card-header bg-success border border-success"></div>
                <div class="card-body">
                    <form @submit.prevent="save">
                        <div class="input-group mb-3">
                            <span class="input-group-text">
                                <i class="fa-solid fa-building"></i>
                            </span>
                            <input autofocus type="text" v-model="form.name" 
                            placeholder="Department" class="form-control"
                            required>
                        </div>
                        <div class="d-grid col-10 mx-auto">
                            <button class="btn btn-dark">
                                <i class="fa-solid fa-save"></i> Save</button>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>