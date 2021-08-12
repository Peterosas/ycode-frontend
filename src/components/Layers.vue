<template>
  <aside
    id="right-panel"
    class="relative bg-gray-800 border-l border-gray-600 h-full w-64 flex flex-col overflow-hidden flex-shrink-0"
  >
      <header
        class="layer-header text-white text-xs font-medium tracking-wide flex justify-between items-center p-2 ">
        <div class="flex items-center leading-5 px-1">
          <h3>Layers</h3>
        </div>
      </header>
      <nav class="items-center leading-5 py-2 text-white layer-nav">
       
        <a href = "#" class="block w-full">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 inline-block" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 20l4-16m2 16l4-16M6 9h14M4 15h14" />
          </svg>
          <span class="inline-block py-2 pl-1 text-sm">New Layer</span>
        </a>
        
        
      </nav>
    
  </aside>
</template>

<script>
import Icon from "./Icon.vue";

export default {
  components: {
    Icon,
  },
};
</script>

<style>
  .layer-header {
    border-bottom: 1px solid rgba(255,255,255,0.3);
  }
</style>