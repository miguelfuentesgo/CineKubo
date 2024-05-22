<template>
    <div class="movieItem" >
        <Card class="card-movie" @click="changeModalVisibility">
            <template #header>
                <img class="poster poster-list" alt="user header" :src="pathImage" />
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

const pathImage = computed(() => "https://image.tmdb.org/t/p/w500"+props.movie.poster_path);

</script>

<style scoped>
    

    .buttons {
        display: flex;
        gap: 3px;
        margin-top: 10px;
    }

    .button {
        width: 100%;
    }

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

    .poster-detail {
        width: 150px;
    }

    .title-movie {
        font-size: 12px;
    }

    .date-movie {
        font-size: 10px;
    }

    .modal {
        width: 200rem;
    }

    .movie-details {
        display: flex;
        justify-content: space-between;
    }

    .movie-info {
        padding: 20px;
    }
</style>