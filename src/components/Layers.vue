<template>
  <aside
    id="right-panel"
    class="relative bg-gray-800 border-l border-gray-600 h-full w-64 flex flex-col overflow-hidden flex-shrink-0"
  >
      <header
        class="layer-header text-white text-xs font-medium tracking-wide flex justify-between items-center p-2 ">
        <div class="flex w-full p-2">
          <div class="flex-1">
             <h3>Layers</h3>
          </div>
          <div class="flex-1 text-right">
            <button @click="createLayer">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v3m0 0v3m0-3h3m-3 0H9m12 0a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
            </button>
          </div>
        </div>
      </header>
      <nav class="items-center leading-5 py-2 text-white layer-nav">
        <a href = "#" class="block w-full px-3 py-1 layerlink" @click="selectLayer(index)" v-bind:class="{activeLayer: layerObj == currentLayer}" v-for="(layerObj, index) in layerBag" v-if="currentLayer">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 inline-block" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 20l4-16m2 16l4-16M6 9h14M4 15h14" />
          </svg>
          <span class="inline-block px-4 pl-1 text-sm">{{layerObj.title}}</span>
        </a> 
      </nav>
    
  </aside>
</template>

<script>
import Icon from "./Icon.vue";

export default {
  props: {
    createLayer: Function,
    selectLayer: Function,
    currentLayer: Object,
    layerBag: Array
  },
  components: {
    Icon
  }
};
</script>
<style>
  .layer-header {
    border-bottom: 1px solid rgba(255,255,255,0.3);
  }
  .activeLayer {
    background-color: rgba(255, 255, 255, 0.1);
    color: #fff;
    font-weight: 600;
  }
  .layerlink {
    color: rgba(255, 255, 255, 0.7)
  }
</style>