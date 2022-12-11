<script setup>
const props = defineProps(['data'])
</script>

<template>
<div class="card">
<img class="card-image" :src="data.image"/>
<h1>{{data.name}}</h1>
<p>{{data.status}}</p>
</div>
</template>

<style scoped>

.card { 
    background-color: #333;
    border-radius:4px;
    display:flex;
    flex-direction: column;
    color:white;
    max-width:200px;
}

.card > h1 { 
    font-size:24px;
    margin:8px;
}
.card-image { 
    border-radius:4px;
}
</style>
