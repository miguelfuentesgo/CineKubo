<template>
    <div class="content">
        <SearchBar />
        <MovieList >
    
            <template #items>


                <MovieItem v-for="movie in results" :key="movie.id" :movie="movie"/>
                
            </template>
        </MovieList>
    </div>
   
</template>

<script setup>
const  token = 'eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiI3Y2Q2NTUwYjAxYzU5ZmY5Y2ExNDkwNGE5MTQxNTY3YyIsInN1YiI6IjY2NGUxMjM5NzgxYTZhNWY4YTE4OTFhMSIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.BFbDb1UgrY1D_kdCqsFjUbDSV8CjJgW9gETz4ctGIP4';

const url = 'https://api.themoviedb.org/3/trending/movie/day?language=en-US';
const { data } = await useFetch('https://api.themoviedb.org/3/trending/movie/day?language=en-US', {
    headers: { 'Content-Type': 'application/json', 'Authorization': 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiI3Y2Q2NTUwYjAxYzU5ZmY5Y2ExNDkwNGE5MTQxNTY3YyIsInN1YiI6IjY2NGUxMjM5NzgxYTZhNWY4YTE4OTFhMSIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.BFbDb1UgrY1D_kdCqsFjUbDSV8CjJgW9gETz4ctGIP4'}
})

const results = JSON.parse(JSON.stringify(data.value)).results;

console.log(results);
















</script>
<style scoped>
.content{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

</style>
