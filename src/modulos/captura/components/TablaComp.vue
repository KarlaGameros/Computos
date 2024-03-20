<template>
  <div class="q-pa-lg">
    <q-banner
      inline-actions
      class="text-justify bg-white"
      style="border-radius: 20px"
    >
      <q-btn
        v-model="eleccion"
        flat
        rounded
        color="blue-grey"
        label="Diputaciones"
      />
      <q-btn
        flat
        rounded
        color="blue-grey"
        label="Presidencias y Sindicaturas"
      />
      <q-btn flat rounded color="blue-grey" label="Regidurias" />
    </q-banner>
    <div class="q-pt-lg">
      <q-card>
        <q-tabs
          v-model="tab"
          class="text-grey"
          active-color="blue-grey"
          indicator-color="blue-grey"
          align="justify"
          :breakpoint="0"
        >
          <q-tab
            v-for="cargo in list_Cargo"
            :key="cargo"
            :name="cargo.siglas"
            :label="cargo.nombre"
          />
        </q-tabs>

        <q-separator />

        <q-tab-panels v-model="tab" animated>
          <q-tab-panel name="MR">
            <div class="text-h6 text-grey">
              Listado de casillas sugeridas a recuento
            </div>
            <br />
            <div><TablaComputada /></div>
            <br />
            <q-separator />
            <div class="text-h6 text-grey">
              Listado de casillas sugeridas a cotejo
            </div>
            <br />
            <div><TablaComputada /></div>
          </q-tab-panel>

          <q-tab-panel name="RP">
            <div class="text-h6 text-grey">
              Listado de casillas sugeridas a cotejo
            </div>
            <br />
            <div><TablaComputada /></div>
          </q-tab-panel>
        </q-tab-panels>
      </q-card>
    </div>
  </div>
</template>

<script setup>
import { onBeforeMount, ref } from "vue";
import TablaComputada from "../components/TablaComputada.vue";

//-----------------------------------------------------------

onBeforeMount(() => {});

const list_Cargo = ref([
  { siglas: "MR", nombre: "Mayoria relativa" },
  { siglas: "RP", nombre: "Representación proporcional" },
]);
const tab = ref("MR");
const eleccion = ref("DIP");

const columns = [
  {
    name: "usuario",
    align: "center",
    label: "Usuario",
    field: "usuario",
    sortable: true,
  },
  {
    name: "acuerdo",
    align: "center",
    label: "Acuerdo",
    field: "acuerdo",
    sortable: true,
  },
  {
    name: "fecha_Aprobacion",
    align: "center",
    label: "Fecha aprobación",
    field: "fecha_Aprobacion",
    sortable: true,
  },
  {
    name: "fecha_Registro",
    align: "center",
    label: "Fecha registro",
    field: "fecha_Registro",
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

const filter = ref("");
const pagination = ref({
  sortBy: "desc",
  descending: false,
  page: 1,
  rowsPerPage: 5,
});
</script>

<style></style>
