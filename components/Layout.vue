<template>
    <div class="header">
        <slot name="header"></slot>
    </div>

    <div class="content">
        <slot name="content"></slot>
    </div>
    
</template>


<style scoped>

.header,
.content {
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 14px 0;
  box-sizing: border-box;
}

.content {
    margin: 20px;
}
</style>