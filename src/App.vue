<template>
  <v-app>
    <v-main>
      <data-table></data-table>
    </v-main>
  </v-app> 
</template>

<script>
import DataTable from './components/DataTable';

export default {
  name: 'App',

  components: {
    DataTable,
  },

  data: () => ({
    //
  }),
};
</script>
