<template>
    <header>
        <img src="@/assets/logo.jpeg" alt="logo" @click="reloadPage"/>
        <h1><span>Cine</span>Kubo</h1>
        <span></span>

        
    </header>
    
</template>

<script setup>

const reloadPage = () => {
      // Recargar la página actual
      window.location.reload();
    }
</script>

<style scoped>
header {
    display: flex;
    justify-content: space-around;
    align-items: center;
    width: 100vw;
}

img,
span {
  width: 48px;
}

img {
    cursor: pointer;
}
</style>