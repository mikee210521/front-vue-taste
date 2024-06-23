<template>
  <div>
    <h2>Usuarios</h2>
    <table>
      <thead>
      <tr>
        <th>ID</th>
        <th>Nombre de usuario</th>
        <th>Fecha de nacimiento</th>
        <th>Edad</th>
        <th>Dirección</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="usuario in usuarios" :key="usuario.id">
        <th>{{ usuario.id }}</th>
        <td>{{ usuario.name }}</td>
        <td>{{ usuario.fecha_nacimiento }}</td>
        <td>{{ usuario.edad }}</td>
        <td>{{ concatenarDireccion(usuario.user_domicilio) }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const usuarios = ref([]);

const obtenerUsuarios = async () => {
  try {
    const respuesta = await axios.get('https://databaseusers.000webhostapp.com/api/users');
    usuarios.value = respuesta.data;
  } catch (error) {
    console.error('Error al obtener usuarios:', error);
  }
};

const concatenarDireccion = (direccion) => {
  return `${direccion.domicilio}, ${direccion.numero_exterior}, ${direccion.colonia}, ${direccion.cp}, ${direccion.ciudad}`;
};

onMounted(() => {
  obtenerUsuarios();
});

</script>

<style scoped>
table {
  width: 100%;
  border-collapse: collapse;
  color: red;
}

th, td {
  border: 2px solid #808080;
  padding: 8px;
  text-align: left;
}

th {
  background-color: #f2f2f2;
}
</style>
