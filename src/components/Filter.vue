<template>
    <input type="text" class="form-input" v-model="input" placeholder="Buscar receta..." />
    <a :href="recipe.link" class="form-input__result" v-if="input && filteredList().length"
        v-for="recipe in filteredList()" :key="recipe.name">
        {{ recipe.name }}
    </a>
    <div class="form-input__result error" v-if="input && !filteredList().length">
        <p>No results found!</p>
    </div>
</template>

<script>
import { ref } from "vue";

let input = ref("");
const recipes = [
    { link: 'about', name: 'orange' },
    { link: 'recipe2', name: 'banana' },
    { link: 'recipe3', name: 'apple' },
];

function filteredList() {
    return recipes.filter((recipe) =>
        recipe.name.toLowerCase().includes(input.value.toLowerCase())
    );
}
</script>