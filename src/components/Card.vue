<script setup lang="ts">

const cards = [
    { link: 'recipe1', text: 'card 1', image: 'src/assets/magnify.svg' },
    { link: 'recipe2', text: 'card 2', image: 'src/assets/magnify.svg' },
    { link: 'recipe3', text: 'card 3', image: 'src/assets/magnify.svg' },
];

</script>
<template>
    <a :href="card.link" v-for="card in cards" :key="card.text" class="card">
        <figure>
            <img :src="card.image" :alt="card.image">
        </figure>
        <div>
            <p> {{ card.text }}</p>
        </div>
    </a>
</template>

