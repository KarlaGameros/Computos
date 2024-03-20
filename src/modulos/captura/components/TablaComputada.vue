<template>
  <q-table
    :rows="rows"
    :columns="columns"
    :filter="filter"
    row-key="name"
    v-model:pagination="pagination"
    color="pink"
  >
    <template v-slot:top-right>
      <q-input
        borderless
        dense
        debounce="300"
        v-model="filter"
        placeholder="Buscar"
      >
        <template v-slot:append>
          <q-icon name="search" />
        </template>
      </q-input>
    </template>
    <template v-slot:body="props">
      <q-tr :props="props">
        <q-td v-for="col in props.cols" :key="col.name" :props="props">
          <div v-if="col.name === 'id'">
            <q-btn
              flat
              round
              color="pink"
              icon="edit_square"
              @click="recuento(props.row)"
            >
              <q-tooltip>Ver acuerdo</q-tooltip>
            </q-btn>
          </div>

          <label v-else>{{ col.value }}</label>
        </q-td>
      </q-tr>
    </template>
  </q-table>
</template>

<script setup>
import { ref } from "vue";
//import Swal from "sweetalert2";

//-------------------------------------------------------

const columns = [
  {
    name: "municipio",
    align: "center",
    label: "Municipio",
    field: "municipio",
    sortable: true,
  },
  {
    name: "demarcacion",
    align: "center",
    label: "Demarcación",
    field: "demarcacion",
    sortable: true,
  },
  {
    name: "seccion",
    align: "center",
    label: "Sección",
    field: "seccion",
    sortable: true,
  },
  {
    name: "casilla",
    align: "center",
    label: "Casilla",
    field: "casilla",
    sortable: true,
  },
  {
    name: "causales",
    align: "center",
    label: "No. Causales",
    field: "causales",
    sortable: true,
  },
  {
    name: "id",
    align: "center",
    label: "Acciones",
    field: "id",
    sortable: true,
  },
];
const rows = ref([
  {
    municipio: "municipio",
    demarcacion: "demarcacion",
    seccion: "seccion",
    casilla: "casilla",
    causales: 3,
    id: 1,
  },
]);
const filter = ref("");
const pagination = ref({
  sortBy: "desc",
  descending: false,
  page: 1,
  rowsPerPage: 5,
});

//-------------------------------------------------------

// const recuento = () => {
//   Swal.fire({
//     title: "¿Se han reservado votos en esta casilla para esta elección?",
//     icon: "warning",
//     showCancelButton: true,
//     cancelButtonText: "No",
//     confirmButtonColor: "#3085d6",
//     cancelButtonColor: "#d33",
//     confirmButtonText: "Si",
//   }).then((result) => {
//     if (result.isConfirmed) {
//       tipoRecuento();
//     }
//   });
// };

// const tipoRecuento = () => {
//   Swal.fire({
//     title: "Tipo de cómputo",
//     input: "select",
//     inputLabel: "Se sugiere recuento",
//     inputOptions: {
//       recuento: "Recuento",
//     },
//     inputPlaceholder: "Selecciona una opción",
//     showCancelButton: true,
//     cancelButtonText: "Cancelar",
//     confirmButtonColor: "#3085d6",
//     cancelButtonColor: "#d33",
//     confirmButtonText: `Siguiente&nbsp;<i class="fa fa-arrow-right"></i> `,
//     inputValidator: (value) => {
//       return new Promise((resolve) => {
//         if (value != "") {
//           resolve();
//         } else {
//           resolve("Se necesita seleccionar una opción:)");
//         }
//       });
//     },
//   }).then((result) => {
//     if (result.isConfirmed) {
//     }
//   });
// };
</script>

<style></style>
