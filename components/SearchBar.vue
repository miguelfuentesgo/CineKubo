<template>
    <Message :closable="false" severity="error" v-if="errorSearch">Please, enter a valid name</Message>
    <FloatLabel>
        <InputText id="movie"  v-model="inputSearch" />
        <label for="movie">Movie</label>
        <Button label="Search" @click="handleSearch"></Button>
    </FloatLabel>
</template>

<script setup>


import InputText from 'primevue/inputtext';
import IconField from 'primevue/iconfield';
import InputIcon from 'primevue/inputicon';

const inputSearch = ref("");
const errorSearch = ref(false)

const emit = defineEmits(['emitSearch'])
const handleSearch = ()  => {
    console.log('input search', inputSearch);
    errorSearch.value = false;
    if(inputSearch.value == ""){
        console.log('input search', inputSearch);
        errorSearch.value = true;
    } else {
        emit('emitSearch', inputSearch.value)

    }
   
}
</script>