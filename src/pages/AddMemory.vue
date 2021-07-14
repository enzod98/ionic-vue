<template>
  <base-layout pageTitle="Agregar un nuevo recuerdo" defaultBackPage="/memories">
    <create-memory-form @save-memory="addMemory"></create-memory-form>
  </base-layout>
</template>

<script>
import CreateMemoryForm from '../components/memories/CreateMemoryForm.vue'
export default {
  components:{
    CreateMemoryForm
  },
  methods: {
    addMemory(memoryData) {
      this.$store.dispatch('addMemory', memoryData);
      this.$router.replace('/memories');  //replace se usa para asegurar que no se pueda navegar atrás
    }
  },
}
</script>
