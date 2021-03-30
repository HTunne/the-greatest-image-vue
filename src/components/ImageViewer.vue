<template>
  <div class="image-viewer">
      <v-img
      height=100
      width=100
      :src='imageSrc'
      >
      </v-img>
      <v-btn
      :click='postAnswer(yes)'
      elevation="2"
      >Yes</v-btn>
      <v-btn
      :click='postAnswer(no)'
      elevation="2"
      >No</v-btn>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'ImageViewer',
  methods: {
    async getImage() {
      this.imaageLoaded = false;
      let axios_conf = {
        baseURL: this.baseURL,
        method: 'get'
      }
      let response = await axios(axios_conf);
      console.log(response);
      this.imageName = response.data['img']
      this.imageLoaded = true;
    },
    async postAnswer(answer) {
      let axios_conf = {
        baseURL: this.baseURL,
        method: 'get',
        data: {
          uuid: 'test-uuid',
          response: answer
        }
      }
      let response = await axios(axios_conf);
      console.log(response);
    }
  },
  computed: {
    imageSrc() {
      if (this.imageName)
        return this.baseURL + '/static/img/' + this.imageName;
      return null;
    }
  },
  created() {
    this.getImage()
  },
  data: () => ({
    baseURL: 'http://localhost:5000',
    imageLoaded: false,
    imageName: null,
  }),
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
