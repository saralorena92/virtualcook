<script setup lang="ts">
import Filter from "../components/Filter.vue";
import Tab from "../components/Tab.vue";
import Card from "../components/Card.vue";

const tabList = ["Todo", "Comidas", "Cenas", "Vegetariano", "Repostería", "Otros"];


</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Inicio</RouterLink>
    </nav>
  </header>
  <main class="wrapper">

    <h1 class="title">Menu</h1>
    <p class="text">¿Qué quieres cocinar hoy? El recetario virtual con todas las recetas.</p>

    <Filter />

    <div>
      <Tab :tabList="tabList">
        <template v-slot:tabPanel-1>
          <div class="card__grid">
            <Card />
          </div>
        </template>
        <template v-slot:tabPanel-2> Content 2 </template>
        <template v-slot:tabPanel-3> Content 3 </template>
        <template v-slot:tabPanel-4> Content 4 </template>
        <template v-slot:tabPanel-5> Content 5 </template>
        <template v-slot:tabPanel-6> Content 6 </template>
      </Tab>
    </div>

  </main>
</template>



