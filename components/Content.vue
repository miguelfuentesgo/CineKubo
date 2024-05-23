<template>
    <div class="content">
        <SearchBar  @emitSearch="handleSearch" />
        <MovieList >
    
            <template #items>
                <Loading v-if="pendingMovies"/>
                <h1 v-show="errorMovies"> Error loading movies</h1>
                <MovieItem v-show="!pendingMovies" v-for="movie in movies" :key="movie.id" :movie="movie"/>

                
            </template>
        </MovieList>
    </div>
   
</template>

<script setup>

const movies = ref([])
const pendingMovies = ref(true);
const errorMovies = ref(false);

const  token = 'eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiI3Y2Q2NTUwYjAxYzU5ZmY5Y2ExNDkwNGE5MTQxNTY3YyIsInN1YiI6IjY2NGUxMjM5NzgxYTZhNWY4YTE4OTFhMSIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.BFbDb1UgrY1D_kdCqsFjUbDSV8CjJgW9gETz4ctGIP4';

const url = 'https://api.themoviedb.org/3/trending/movie/day?language=en-US';

const urlSearch = 'https://api.themoviedb.org/3/search/movie?include_adult=false&language=en-US&page=1'


const { data, error } = await useFetch(url, {
    headers: { 'Content-Type': 'application/json', 'Authorization': 'Bearer '+token}
})

movies.value = JSON.parse(JSON.stringify(data.value)).results;
pendingMovies.value = false;

if(errorMovies.value) {
    errorMovies.value = true;
}



const handleSearch = async (search) => {
    pendingMovies.value = true;
    console.log("buscando... ", search  )

    const { data } = await useFetch(urlSearch, {
    headers: { 'Content-Type': 'application/json', 'Authorization': 'Bearer '+token},
    query: { query: String(search)}

    
})
    console.log('searched...')
    console.log(data.value)
    movies.value = JSON.parse(JSON.stringify(data.value)).results;
    pendingMovies.value = false
}
</script>
<style scoped>
.content{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

</style>
