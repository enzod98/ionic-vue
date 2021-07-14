<template>
  <base-layout
    :pageTitle="loadedMemory ? loadedMemory.title : 'Cargando...'"
    defaultBackPage="/memories"
  >
    <h2 v-if="!loadedMemory">No se encontró su recuerdo</h2>
    <memory-overview
    v-else
    :title="loadedMemory.title"
    :img="loadedMemory.img"
    :description="loadedMemory.description"
    />
  </base-layout>
</template>

<script>
import MemoryOverview from "../components/memories/MemoryOverview.vue";

export default {
  components: {
    MemoryOverview,
  },
  data() {
    return {
      memoryId: this.$route.params.id,
    };
  },
  computed: {
    loadedMemory() {
      return this.$store.getters.memory(this.memoryId);
    },
  },
};
</script>