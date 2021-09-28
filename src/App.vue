<template>
  <v-app>
    <div class="d-flex justify-center font-weight-medium mt-4 text-h5">
      <span style="color: #fff; background: #31c2ff" class="rounded pa-1 px-4">
        Mynul
      </span>
    </div>

    <v-main>
      <Calculator />
    </v-main>
  </v-app>
</template>

<script>
import Calculator from "./components/Calulator.vue";

export default {
  name: "App",

  components: {
    Calculator,
  },

  data: () => ({
    //
  }),
};
</script>
