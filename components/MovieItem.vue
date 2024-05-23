<template>
    <div class="movieItem" >
        <Card class="card-movie" @click="changeModalVisibility">
            <template #header>
                <div v-if="!imageLoaded" class="container-spinner">
                    <ProgressSpinner />
                </div>
                
                <img class="poster poster-list" alt="Movie poster" ref="posterImage" @load="onLoad()" :src="pathImage"  />
            </template>
            <template #title> <span class="title-movie">{{props.movie.original_title}}</span></template>
            <template #subtitle><span class="date-movie">{{ props.movie.release_date}}</span></template>
        </Card>

        <MovieDetailsModal :modalVisible="modalDetailVisible" @click="changeModalVisibility" :movie="props.movie"/>

        
    </div>
</template>

<script setup >
import MovieDetailsModal from './MovieDetailsModal.vue';




const props = defineProps({
  movie: {
    type: Object,
    required: true
  }
});

const modalDetailVisible = ref(false);

const changeModalVisibility = () => modalDetailVisible.value = !modalDetailVisible.value;

const imageLoaded = ref(false);

const pathImage = computed(function(){
   return  String(props.movie.poster_path).endsWith('null') ? "../assets/logo.jpeg" :"https://image.tmdb.org/t/p/w500"+props.movie.poster_path
});

const onLoad = () => {
    console.log('Imagen cargada');
    imageLoaded.value = true;
}
const posterImage = ref(null);
onMounted(() => {
    
    if (posterImage.value && posterImage.value.complete) {
        imageLoaded.value = true;
      }
  
});

</script>

<style scoped>

    .content {
        margin: 0;
    }

    .card-movie{
        width: 150px;
        height: 390px;
        cursor: pointer;
    }

    .card-movie:hover{
        background-color: #a78bfa;
    }

    



    .poster-list {
        width: 100%;
        height: 100%;
        transition: 0.5s;
        object-fit: cover;
    }

    .poster-list:hover{
        transform: scale(1.2);
    }

    
    .title-movie {
        font-size: 12px;
    }

    .date-movie {
        font-size: 10px;
    }


    @media (max-width: 540px) {
        .card-movie{
            width: 200px;
            height: 300px;
            cursor: pointer;
        }

        .title-movie, .date-movie {
            display: none;
        }

        .poster-list {
            transition: none;
            object-fit: fill;
        }
        .poster-list:hover{
            transform: none;
        }

        .container-spinner {
            width: 200px !important;
            height: 300px !important;
        }

    }

    .container-spinner {
        width: 150px;
        height: 200px;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    
</style>