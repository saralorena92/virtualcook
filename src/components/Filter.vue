<script setup lang="ts">
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
<template>
    <input type="text" class="form-search" v-model="input" placeholder="Buscar receta..." />
    <a :href="recipe.link" class="form-search__result" v-if="input && filteredList().length"
        v-for="recipe in filteredList()" :key="recipe.name">
        {{ recipe.name }}
    </a>
    <div class="form-search__result error" v-if="input && !filteredList().length">
        <p>No results found!</p>
    </div>
</template>

<style>
.form-search {
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    height: 43px;
    border-radius: 5px;
    border: none;
    font-size: 1rem;
    padding: 12px 16px;
    width: 100%;
    font-family: "Montserrat", sans-serif;
    font-weight: 400;
    background: var(--vt-c-white-mute) url("../assets/magnify.svg") no-repeat 98%;
    background-size: auto;
}

.form-search ::-webkit-input-placeholder {
    color: var(--vt-c-dark);
    opacity: .8;
}

.form-search ::-moz-placeholder {
    color: var(--vt-c-dark);
    opacity: .8;
}

.form-search :-ms-input-placeholder {
    color: var(--vt-c-dark);
    opacity: .8;
}

.form-search ::-ms-input-placeholder {
    color: var(--vt-c-dark);
    opacity: .8;
}

.form-search ::placeholder {
    color: var(--vt-c-dark);
    opacity: .8;
}

.form-search:focus-visible,
.form-search:focus {
    border: none;
    outline: none;
    background-color: var(--vt-c-white-soft);
}

.form-search__result {
    width: 100%;
    color: var(--vt-c-dark);
    opacity: .8;
    text-decoration: none;
    border-bottom: 1px solid var(--vt-c-white-mute);
    padding: 1rem 0;
    font-size: 1rem;
}
</style>

