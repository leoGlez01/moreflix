<template>
  <nav class="bg-[#141014ff] pl-4 pr-4 flex flex-row sm:flex-row justify-between align-middle">
    <transition name="slide">
      <div v-if="shouldShowMenu" class="nav-izquierda fixed top-0 left-0 flex flex-col w-64 h-full bg-[#141014ff] overflow-auto text-white lg:static lg:flex lg:flex-row lg:w-auto lg:space-x-4 lg:overflow-visible">
        <button class="m-8 text-white self-start lg:hidden" @click="showMenu = false">Cerrar</button>
        <ul class="m-6 flex flex-col lg:flex-row lg:justify-around lg:space-x-4">
          <li class="m-4 lg:m-0"><a href="#">Inicio</a></li>
          <li class="m-4 lg:m-0"><a href="#">Series</a></li>
          <li class="m-4 lg:m-0"><a href="#">Peliculas</a></li>
          <li class="m-4 lg:m-0"><a href="#">Estrenos</a></li>
          <li class="m-4 lg:m-0"><a href="#">Recomendados</a></li>
        </ul>
      </div>
    </transition>
    <button class="text-white lg:hidden m-4" @click="showMenu = !showMenu">Menu</button>

    <ul class="w-1/2 sm:w-[20%] flex justify-between">
      <input type="text" id="search" 
      class="text-white text-[11px] lg:text-[16px] 
      m-4 w-1/3 lg:w-1/2 pl-2 h-[50%] 
      transition-all duration-500 ease-in-out 
      focus:w-1/2 lg:focus:w-full  focus:outline-none 
      rounded border border-gray-300 bg-inherit" 
      placeholder="Buscar...">
      <li class="m-4 w-[15%] h-[50%]"><a class="text-white" href="#">
        <svg xmlns="http://www.w3.org/2000/svg" height="auto" viewBox="0 -960 960 960" width="auto"><path fill="#fff" d="M234-276q51-39 114-61.5T480-360q69 0 132 22.5T726-276q35-41 54.5-93T800-480q0-133-93.5-226.5T480-800q-133 0-226.5 93.5T160-480q0 59 19.5 111t54.5 93Zm246-164q-59 0-99.5-40.5T340-580q0-59 40.5-99.5T480-720q59 0 99.5 40.5T620-580q0 59-40.5 99.5T480-440Zm0 360q-83 0-156-31.5T197-197q-54-54-85.5-127T80-480q0-83 31.5-156T197-763q54-54 127-85.5T480-880q83 0 156 31.5T763-763q54 54 85.5 127T880-480q0 83-31.5 156T763-197q-54 54-127 85.5T480-80Zm0-80q53 0 100-15.5t86-44.5q-39-29-86-44.5T480-280q-53 0-100 15.5T294-220q39 29 86 44.5T480-160Zm0-360q26 0 43-17t17-43q0-26-17-43t-43-17q-26 0-43 17t-17 43q0 26 17 43t43 17Zm0-60Zm0 360Z"/></svg>
        </a>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'NavBar',
  data() {
    return {
      showMenu: false,
      windowWidth: 0
    };
  },
  computed: {
    shouldShowMenu() {
      return this.showMenu || this.windowWidth >= 1024;
    }
  },
  mounted() {
    window.addEventListener('click', (event) => {
      if (!this.$el.contains(event.target)) {
        this.showMenu = false;
      }
    });
    window.addEventListener('resize', this.updateWindowWidth);
    this.updateWindowWidth();
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.updateWindowWidth);
  },
  methods: {
    updateWindowWidth() {
      this.windowWidth = window.innerWidth;
    },
  },
};
</script>

<style scoped>
.slide-enter-active, .slide-leave-active {
  transition: all .3s ease;
}
.slide-enter-from, .slide-leave-to {
  transform: translateX(-100%);
}
</style>
