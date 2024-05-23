<template>
   
        <Card id="card-movie" v-for="(item, index) in 7"/>
    
</template>


<style scoped>
#card-movie{
    width: 150px;
    height: 390px;
    background: linear-gradient(90deg, #202738, #a78bfa);
    background-size: 400% 400%;
    animation: loadingAnimation 3s ease-in-out infinite;
    
}

@keyframes loadingAnimation {
    0% {
      background-position: 0% 50%;
    }
    50% {
      background-position: 100% 50%;
    }
    100% {
      background-position: 0% 50%;
    }
  }

  @media (max-width: 540px) {
    #card-movie{
        width: 200px;
        height: 300px;
    }
}

</style>