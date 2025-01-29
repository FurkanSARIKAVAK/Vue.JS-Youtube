<template>
  <div v-if="video" class="selectedVideoContainer">
    <div>
      <iframe class="selectedVideo" :src="videoUrl"></iframe>
    </div>
    <div class="details">
      <h4 v-html="video.snippet.title"></h4>
      <p v-html="video.snippet.description"></p>
    </div>
  </div>
</template>
  
  <script>
export default {
  props: ["video"],
  computed: {
    videoUrl() {
      const { videoId } = this.video.id;
      return `https://www.youtube.com/embed/${videoId}`;
    },
  },
};
</script>

<style scoped>
.selectedVideoContainer{
    width: 100%;
}
.selectedVideo{
    width: 100%;
    height: 350px;
}
.details{
    border: 1px solid gray;
    border-radius: 4px;
    padding: 10px;
    margin-top: 10px;
}
.details h4 {
  font-size: 25px;
  margin: 10px 0px;
}
.details p {
  font-size: 18px;

}
</style>