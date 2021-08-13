<template>
  <aside
    id="right-panel"
    class="relative bg-gray-800 border-l border-gray-600 h-full w-64 flex flex-col overflow-hidden flex-shrink-0"
  >
      <header
        class="text-white text-xs font-medium tracking-wide flex justify-between items-center p-3 pb-0 ">
        <div class="flex items-center leading-5 py-px">Design</div>
      </header>

      <section class="px-4 py-8">
          <div class="mb-4">
            <label class="block input-label text-sm mb-1" for="fontSize">
              Font Size
            </label>
          </div>

          <div class = "flex">
              <input class="inline-block input bg-transparent appearance-none w-full leading-tight focus:bg-black p-2 focus:outline-none focus:shadow-outline" id="fontSize" type="text" placeholder="0px">
              <select class="inline-block input appearance-none pr-8 leading-tight focus:outline-none hover:bg-black focus:bg-black focus:border-gray-800" id="unit">
                <option>px</option>
                <option>rem</option>
              </select>
          </div>
      </section>
    
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
  .input-label {
    color: rgba(255, 255, 255, 0.5);
  }
  .input {
    color: rgba(255, 255, 255, 0.7);
    background: transparent;
    padding: 1px 2px;
  }
</style>