<template>
  <v-app>
    <v-main>
      <navbar/>
    
    </v-main>
  </v-app>
</template>

<script>
import navbar from './components/navbar';

export default {
  name: 'App',
  components: {
    navbar,
    
  },

  data: () => ({
    //
  }),
};
</script>
