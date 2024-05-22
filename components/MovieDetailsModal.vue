<template>
    <Dialog v-model:visible="props.modalVisible" modal :style="{ width: '50rem' }" :header="props.movie.original_title">
        <div class="movie-details">
            <img class="poster-detail" alt="user header" :src="pathImage"/>
            <div class="movie-info">
                <p> {{props.movie.overview}}</p>
            <p> {{ props.movie.release_date}}</p>
            <p> {{ props.movie.vote_average}}</p>
            </div>
        </div>
      

    </Dialog>
</template>

<script setup>

    import Dialog from 'primevue/dialog';

    const props = defineProps({
        modalVisible: {
        type: Boolean,
        required: true,
        }, 
    
        movie: { 
            type: Object,
            required: true
        }
    }

    
    );

    const pathImage = computed(() => "https://image.tmdb.org/t/p/w500"+props.movie.poster_path);
</script>

<style scoped>

.poster-detail {
    width: 150px;
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