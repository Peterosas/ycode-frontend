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

      <Design :currentLayer="currentLayer" />
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
      //Create a new canvas
      const layerCanvas = this.createEditableCanvas("canvas" + this.layerBag.length + 1);
      
      //Make the new layer current
      this.currentLayer = {
        title: 'Layer ' + (this.layerBag.length + 1), 
        content: layerCanvas,
        layerProps: {
          fontSize: "12",
          unit: "px",
          backgroundColor: "bg-white",
          opacity: 10
        }
      };

      //Save new layer in front of the queue
      this.layerBag.unshift(this.currentLayer);

      //Render canvas in layer
      this.$refs.layers.innerHTML = this.currentLayer.content.innerHTML;
    },
    selectLayer(index) {
      this.currentLayer = this.layerBag?.[index];
      this.$refs.layers.innerHTML = this.currentLayer?.content;
    },
    
    createEditableCanvas(id) {
      const canvas = document.createElement("canvas");
      canvas.width = "100%";
      canvas.height = "100%";
      canvas.id = id;
      canvas.style.border = "2px solid black";
      return canvas;
    }
  },
  mounted() {
    
  }
};
</script>
