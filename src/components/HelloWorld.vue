<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div>
      <input type="file" @change="cargarImagen" ref="archivo">
    <button @click="guardarImagen">Guardar imagen</button>
  </div>
    
  </div>
</template>

<script>
//import axios from 'axios';

export default {
  name: 'HelloWorld',
  data() {
    return {
      imagen: null,
      archivo: null
    }
  },
  props: {
    msg: String
  },
  methods: {
    cargarImagen() {
      this.archivo = this.$refs.archivo.files[0];
      const reader = new FileReader();
      reader.addEventListener('load', () => {
        this.imagen = reader.result;
      });
      reader.readAsDataURL(this.archivo);
    },
    guardarImagen() {
      const ruta = './assets/imagenes/imagen.jpg'; // Cambiar por la ruta deseada
      localStorage.setItem(ruta, this.imagen);
      console.log('Imagen guardada en la ruta local.');
    } 
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
