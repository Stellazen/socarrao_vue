<template>
   <button class="button" :style="{ backgroundColor: cor }" type="button">
        {{ nome }}
    </button>
</template>

<script setup>
defineProps({
  nome: String,
  cor: String
})
</script>

<style scoped>
.button{
    width: 200px;
    height: 30px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}
</style>