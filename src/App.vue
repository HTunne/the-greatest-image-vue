<template>
  <v-app>
    <v-main>
    <ImageViewer/>
    </v-main>
  </v-app>
</template>

<script>
import ImageViewer from '@/components/ImageViewer.vue';

export default {
  name: 'App',

  components: {
    ImageViewer
  },
};
</script>
