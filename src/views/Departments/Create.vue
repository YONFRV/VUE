<script setup>
import {ref,nextTick} from 'vue';
import { sendRequest } from '../../functions';
import { useAuthStore } from '../../stores/auth';
const authStore = useAuthStore();
axios.defaults.headers.common['Authorization'] = 'Bearer '+authStore.authToken;
const form = ref({ name:'' });
const nameInput = ref('');
const save = () =>{
    sendRequest('POST',form.value,'/api/departments','');
    form.value.name = '';
    nextTick( () => nameInput.value.focus());
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
                            required ref="nameInput">
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
