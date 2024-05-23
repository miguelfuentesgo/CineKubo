<template
>

<div class="movieList">
    <slot name="items" />
</div>



</template>


<style scoped>

.movieList {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    margin-top: 25px;
    justify-content: center;
}
</style>
