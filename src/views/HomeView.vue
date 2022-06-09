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
      <tab :tabList="tabList">
        <template v-slot:tabPanel-1> Content 1 </template>
        <template v-slot:tabPanel-2> Content 2 </template>
        <template v-slot:tabPanel-3> Content 3 </template>
        <template v-slot:tabPanel-4> Content 4 </template>
      </tab>
    </div>

  </main>
</template>

<script>
import Filter from "@/components/filter.vue";
import Tab from "@/components/Tab.vue";

export default {
  components: {
    Tab,
  },

  data() {
    return {
      tabList: ["Todo", "Carnes", "Vegetariano", "Postres"],
    };
  },
};
</script>

