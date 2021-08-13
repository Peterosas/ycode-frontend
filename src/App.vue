<template>
  <main class="h-screen w-screen overflow-hidden bg-white flex flex-col">
    <NavBar />
    <section class="relative flex flex-1 flex-row overflow-hidden">
      <Layers :createLayer="createLayer" :selectLayer="selectLayer" :layerBag="layerBag" :currentLayer="currentLayer" />
      <section
        class="w-full h-full relative z-10 scrollbar text-center text-none overflow-auto"
      >
        <div ref="layers" class="p-4"></div>
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
      currentLayer: null,
      lastActiveLayer: null
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

      //Make active
      this.selectLayer(this.layerBag.length + 1);

      //Render canvas in layer
      this.$refs.layers.appendChild(this.currentLayer.content);
    
    },
    selectLayer(index) {
      //Validate index
      if (index >= this.layerBag.length) return;

      //Clear active style
      if (this.lastActiveLayer) {
          this.lastActiveLayer.content.style.border = "2px solid #000";
          this.lastActiveLayer.content.style.zIndex = 0;
      }

      const layer  = this.layerBag[index];
      const canvas = layer.content;

      //Select layer styles
      canvas.style.border = "2px solid blue";
      canvas.style.zIndex = -1;

      this.currentLayer = layer;
      this.lastActiveLayer = this.currentLayer;
    },
    
    createEditableCanvas(id) {
      const canvas = document.createElement("canvas");
      canvas.style.position = "absolute";
      canvas.style.width = "200px";
      canvas.style.height = "200px";
      canvas.id = id;
      canvas.style.border = "2px solid black";
      return canvas;
    }
  },
  mounted() {
    
  }
};
</script>
