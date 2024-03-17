<script>
  import NavBar from './components/NavBar.vue';

  export default {
    components: {
      NavBar
    }
  }
</script>

<template>
  <div class="min-h-screen bg-[#252025]">
    <NavBar/>
    <div class="flex-col justify-start">
      <h1 class="text-white font-bold ml-8 mt-10 text-[24px]">Reproducidas Recientemente</h1>
      <div class="ml-8 mr-8 mt-6 grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
        <div class="size-auto"><img class="size-full" src="./img/film.jfif" alt="img"></div>
        <div class="size-auto"><img class="size-full" src="./img/film1.jfif" alt="img"></div>
        <div class="size-auto"><img class="size-full" src="./img/film2.jfif" alt="img"></div>
        <div class="size-auto"><img class="size-full" src="./img/film3.jfif" alt="img"></div>
      </div>
    </div>
  </div>
</template>
