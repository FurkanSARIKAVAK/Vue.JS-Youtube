<template>
  <div class="container">
      <h1 class="title">
        YouTube <img class="youtube-icon" src="./assets/youtube-icon.svg" />
      </h1>
    <SearchBar @termChange="onTermChange" />
    <div class="detailDiv">
      <VideoDetail :video="selectedVideo" />
      <VideoList @videoSelect="onVideoSelect" :videos="videos" />
    </div>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar.vue";
import VideoList from "./components/VideoList.vue";
import VideoDetail from "./components/VideoDetail.vue";
import axios from "axios";
export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail,
  },
  data() {
    return {
      videos: [],
      selectedVideo: null,
    };
  },
  methods: {
    onVideoSelect(video) {
      this.selectedVideo = video;
    },
    onTermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            part: "snippet",
            type: "video",
            key: "AIzaSyBgEoQbbHxQ3WbBw7PCU4h2r3V-96Y8MmU",
            q: searchTerm,
          },
        })
        .then((response) => {
          this.videos = response.data.items;
          console.log(this.videos);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.container {
  max-width: 1200px;
  width: 100%;
  margin: 50px auto;
}

.container h1 {
  font-family: Arial, Helvetica, sans-serif;
}

.title {
  display: flex;
  text-align: center;
  justify-content: center;
}

.detailDiv {
  display: flex;
}

.youtube-icon {
  width: 35px;
  margin: 0px 10px;
}
</style>
