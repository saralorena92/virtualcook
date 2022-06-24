<script setup lang="ts">
import { ref } from "vue";

let input = ref("");
let inputTodo = 'Todo';
let inputComida = 'comida';

const recipes = [
    { name: 'recipe1', image: 'src/assets/magnify.svg', link: 'recipe1', category: 'comida' },
    { name: 'recipe2', image: 'src/assets/magnify.svg', link: 'recipe2', category: 'postres' },
    { name: 'recipe3', image: 'src/assets/magnify.svg', link: 'recipe3', category: 'cena' },
    { name: 'recipe4', image: 'src/assets/magnify.svg', link: 'recipe4', category: 'vegetariano' },
    { name: 'recipe5', image: 'src/assets/magnify.svg', link: 'recipe5', category: 'comida' },
    { name: 'recipe6', image: 'src/assets/magnify.svg', link: 'recipe6', category: 'cena' }
];

function filteredList() {

    return recipes.filter((recipe) =>
        recipe.name.toLowerCase().includes(input.value.toLowerCase())
    );
}

</script>
<template>
    <input type="text" class="form-search" v-model="input" placeholder="Buscar receta..." />
    <div>
        <label for="all">Todos</label>
        <input id="all" type="radio" v-model="inputTodo" name="category">
    </div>
    <div>
        <label for="comida">Comida</label>
        <input id="comida" type="radio" v-model="inputComida" name="category">
    </div>

    <table>
        <tbody>
            <div class="row">
                <div class="col-2" v-for="recipe in filteredList()">
                    <a :href="recipe.link">
                        <figure>
                            <img :src="recipe.image" :alt="recipe.image">
                        </figure>
                        <span>{{ recipe.category }}</span>
                        <p>
                            {{ recipe.name }}
                        </p>
                    </a>
                </div>
            </div>
            <div class="row" v-if="input && !filteredList().length">
                <div class="col">
                    <p>No results found!</p>
                </div>
            </div>
        </tbody>
    </table>
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

