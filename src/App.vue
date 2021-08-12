<template>
  <main class="h-screen w-screen overflow-hidden bg-white flex flex-col">
    <NavBar />
    <section class="relative flex flex-1 flex-row overflow-hidden">
      <Layers :createLayer="createLayer" :selectLayer="selectLayer" :layerBag="layerBag" :currentLayer="currentLayer" />
      <section
        class="w-full h-full relative z-10 scrollbar text-center text-none overflow-auto"
      >
        <div ref="layers"></div>
      </section>

      <Design />
    </section>
  </main>
</template>

<script>
import Design from "./components/Design.vue";
import Layers from "./components/Layers.vue";
import NavBar from "./components/NavBar.vue";

export default {
  name: "App",
  components: {
    Design,
    NavBar,
    Layers
  },
  data() {
    return {
      layerBag: [],
      currentLayer: null
    }
  },
  methods: {
    createLayer() {
      const layerCanvas = `<div>Hi, I am a layer ${this.layerBag.length + 1}👋🏼</div>`;
      this.currentLayer = {title: 'Layer ' + (this.layerBag.length + 1), content: layerCanvas};
      this.layerBag.unshift(this.currentLayer);
      this.$refs.layers.innerHTML = this.currentLayer.content;
    },
    selectLayer(index) {
      this.currentLayer = this.layerBag?.[index];
      this.$refs.layers.innerHTML = this.currentLayer?.content;
    }
  },
  mounted() {
    
  }
};
</script>
