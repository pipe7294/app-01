<template>
  <div id="app">
    <form @submit.prevent="agregarRegistro">

      <div>
        <label for=""
          :class="{ 'text-red': registro_input.usuario == null || registro_input.usuario == '' }">Usuario</label>
        <input type="text" v-model="registro_input.usuario">
      </div>
      <div>
        <label for="" :class="{ 'text-red': registro_input.fecha == null || registro_input.fecha == '' }">Fecha</label>
        <input type="date" name="" id="" v-model="registro_input.fecha">
      </div>

      <div>
        <label for="" :class="{ 'text-red': registro_input.hora == null || registro_input.hora == '' }">Hora</label>
        <input type="time" name="" id="" v-model="registro_input.hora">
      </div>

      <div>
        <label for=""
          :class="{ 'text-red': registro_input.severidad == null || registro_input.severidad == '' }">Severidad</label>
        <select name="" id="" v-model="registro_input.severidad">
          <option value="1">Baja severidad</option>
          <option value="2">Media severidad</option>
          <option value="3">Alta severidad</option>
        </select>
      </div>

      <div>
        <label for=""
          :class="{ 'text-red': registro_input.observaciones == null || registro_input.observaciones == '' }">Obsevaciones</label>
        <input type="text" v-model="registro_input.observaciones">
      </div>

      <button :disabled="(registro_input.usuario == null || registro_input.usuario == '') ||
        (registro_input.fecha == null || registro_input.fecha == '') ||
        (registro_input.hora == null || registro_input.hora == '') ||
        (registro_input.severidad == null || registro_input.severidad == '') ||
        (registro_input.observaciones == null || registro_input.observaciones == '')
        ">Agregar ticket</button>
    </form>

    {{ registros }}
    <p v-if="registros.length == 0">No hay registros</p>
    <div v-for="(registro, indice) in registros" :key="indice">
      <CardRegistro :usuario="registro.usuario" :fecha="registro.fecha" :hora="registro.hora"
        :severidad="registro.severidad" :observaciones="registro.observaciones" @eliminarRegistro="eliminar(indice)" />
    </div>
  </div>
</template>

<script>
import CardRegistro from './components/CardRegistro.vue'

export default {
  name: 'App',
  data() {
    return {
      registros: [],
      registro_input: {}
    }
  },
  methods: {
    agregarRegistro() {
      this.registros.push(this.registro_input)
      this.registro_input = {};
    },
    eliminar(indice) {
      this.registros.splice(indice, 1)
    }
  },
  components: {
    CardRegistro
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.text-red {
  color: red;
}
</style>
