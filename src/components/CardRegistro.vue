<template>
    <div class="usuario-card">
        <div
            :class="{ 'avatar-container-red': severidad == 3, 'avatar-container-green': severidad == 1, 'avatar-container-yellow': severidad == 2 }">
            <h3>Usuario</h3>
            <p>{{ usuario }}</p>
            <h3>Fecha</h3>
            <p>{{ fecha }}</p>
            <h3>Hora</h3>
            <p>{{ hora }}</p>
            <h3>Observaciones</h3>
            <p>{{ observaciones }}</p>
        </div>
        <div class="boton-container">
            <button @click="eliminarUsuario" class="btn-eliminar">Eliminar</button>
        </div>
    </div>
</template>

<script>
export default {
    props: ["usuario", "fecha", "hora", "severidad", "observaciones"],
    methods: {
        eliminarUsuario() {
            this.$emit('eliminarRegistro');
        }
    }
}
</script>

<style scoped>
.usuario-card {

    border: 1px solid #ccc;
    margin-bottom: 10px;
    width: 200px;
    /* Ancho fijo para mantener el tamaño consistente */
}

.avatar-container-red {
    padding: 10px;
    background-color: red;
    color: white;
}

.avatar-container-green {
    padding: 10px;
    background-color: green;

}

.avatar-container-yellow {
    padding: 10px;
    background-color: yellow;
}

.avatar {
    width: 100%;
    height: auto;
    border-radius: 5px 5px 0 0;
    /* Bordes redondeados solo arriba */
}

.boton-container {
    text-align: center;
    padding: 10px;
}

.btn-eliminar {
    background-color: #f44336;
    color: white;
    border: none;
    padding: 5px 10px;
    cursor: pointer;
}
</style>
