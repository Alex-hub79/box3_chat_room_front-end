<template>
  <v-app>
    
    <v-main>
      <chat/>
    </v-main>
  </v-app>
</template>

<script>
import chat from './components/chat';

export default {
  name: 'App',

  components: {
    chat,
  },

  data: () => ({
    //
  }),
};
</script>