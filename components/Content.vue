<template>
    <FloatLabel>
        <InputIcon class="pi pi-search"> </InputIcon>
        <InputText id="username"  v-model="inputSearch" />
        <label for="username">Movie</label>
        <Button label="Search"></Button>
    </FloatLabel>
</template>

<script setup>


import InputText from 'primevue/inputtext';
import IconField from 'primevue/iconfield';
import InputIcon from 'primevue/inputicon';

const inputSearch = ref("");
</script>