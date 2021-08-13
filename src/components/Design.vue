<template>
  <aside
    id="right-panel"
    class="relative bg-gray-800 border-l border-gray-600 h-full w-64 flex flex-col overflow-hidden flex-shrink-0"
  >
      <header
        class="text-white text-xs font-medium tracking-wide flex justify-between items-center p-3 pb-0 ">
        <div class="flex items-center leading-5 py-px">Design</div>
      </header>

      <section class="px-4 py-8" v-if="currentLayer">
          <div>
            <div class="mb-2">
              <label class="block input-label mb-1" for="fontSize">
                Font Size
              </label>
            </div>

            <div class = "flex">
                <input 
                  class="inline-block input bg-transparent appearance-none w-full leading-tight focus:bg-black p-2 focus:outline-none focus:shadow-outline" 
                  id="fontSize" type="text" 
                  placeholder="0px"
                  v-model="currentLayer.layerProps.fontSize"
                >
                <select v-model="currentLayer.layerProps.unit" class="inline-block input appearance-none pr-8 leading-tight focus:outline-none hover:bg-black focus:bg-black focus:border-gray-800" id="unit">
                  <option>px</option>
                  <option>rem</option>
                </select>
            </div>
          </div>

          <div class="mt-4">
            <div class="mb-2">
              <label class="block input-label mb-1" for="opacity">
                Opacity
              </label>
            </div>

            <div class = "flex">
                <select v-model="currentLayer.layerProps.opacity" class="inline-block p-2 bg-transparent input appearance-none pr-8 leading-tight focus:outline-none hover:bg-black focus:bg-black focus:border-white" id="opacity">
                  <option v-for="n in [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]">{{n}}</option>
                </select>
                <label class="inline-block p-2 input-label" for="opacity">
                  %
                </label>
            </div>
          </div>

          <div class="mt-4">
            <div class="mb-2">
              <label class="block input-label mb-1" for="bgColor">
                Background Color
              </label>
            </div>

            <div class = "flex">
                <div class = "color-box" v-bind:class="currentLayer.layerProps.backgroundColor"></div>                
            </div>
          </div>
      </section>
    
  </aside>
</template>

<script>
import Icon from "./Icon.vue";

export default {
  props: {
    currentLayer: Object
  },
  components: {
    Icon,
  },
};
</script>

<style>
  .input-label {
    color: rgba(255, 255, 255, 0.5);
    font-size: 12px;
  }
  .input {
    color: rgba(255, 255, 255, 0.7);
    background: transparent;
    padding: 1px 2px;
  }
  .color-box {
    width: 30px;
    height: 30px;
    border-radius: 8px;
  }
</style>