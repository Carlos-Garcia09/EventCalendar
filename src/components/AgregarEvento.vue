<template>
    <div>
      <h2>Agregar Evento</h2>
      <form @submit.prevent="agregarEvento">
        <label for="titulo">Título:</label>
        <input type="text" id="titulo" v-model="nuevoEvento.titulo" required>
        <label for="fecha">Fecha:</label>
        <input type="date" id="fecha" v-model="nuevoEvento.fecha" required>
        <button type="submit">Guardar</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        nuevoEvento: {
          titulo: "",
          fecha: "",
        },
      };
    },
    methods: {
      agregarEvento() {
        // Aquí debes emitir un evento personalizado para enviar los datos del nuevo evento al componente del calendario.
        this.$emit("nuevo-evento", this.nuevoEvento);
        // Limpia el formulario
        this.nuevoEvento.titulo = "";
        this.nuevoEvento.fecha = "";
      },
    },
  };
  </script>
  
  <style scoped>
  /* Estilos personalizados para el formulario */
  </style>
  