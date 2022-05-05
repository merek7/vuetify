<template>
  <v-container>
    <v-card color="basil">
      <v-card-title class="text-center justify-center py-6">
        <h1 class="font-weight-bold text-h2 basil--text">TITRE</h1>
      </v-card-title>

      <v-tabs v-model="tab" background-color="transparent" color="basil" grow>
        <v-tab v-for="item in items" :key="item">
          {{ item }}
        </v-tab>
      </v-tabs>

      <v-tabs-items v-model="tab">
        <v-tab-item v-for="item in items" :key="item">
          <v-card color="basil" flat>
            <v-card-text>
                <datatable/>
            </v-card-text>
          </v-card>
        </v-tab-item>
      </v-tabs-items>
    </v-card>
  </v-container>
</template>
<script>
import datatable from "@/components/table.vue";
export default {
    name:'TaB',
    components:{
        datatable
    },
     data () {
      return {
        tab: null,
        items: [
          'Appetizers'
        ],
        
      }
    },
  }

</script>

<style scoped>
/* Helper classes */
.basil {
  background-color: #FFFBE2 !important;
}
.basil--text {
  color: black !important;
}
</style>