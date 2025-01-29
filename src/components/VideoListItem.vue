<template>
  <div>
    <li class="videoItem" @click="onVideoSelect(video)">
        <img class="videoImg" :src="imageUrl">
        <div class="video-title" v-html="video.snippet.title">

        </div>
    </li>
  </div>
</template>

<script>
export default {
    props:['video'],
    emits:['videoSelect'],
    computed:{
        imageUrl(){
            return this.video.snippet.thumbnails.medium.url;
        },
    },
    methods: {
        onVideoSelect(){
            this.$emit('videoSelect', this.video)
        }
    },
}
</script>

<style scoped>
.videoItem {
    display: flex;
    border: 1px solid gray;
    border-radius: 25px;
    margin: 20px;
    box-shadow: rgba(0, 0, 0, 0.4) 0px 5px 15px;
    align-items: center;
}
.videoImg {
    border-radius: 25px 0px 0px 25px;
    margin-right: 20px;
}
.video-title {
  font-size: 18px;
  color: #333;
  font-weight: 600;
}
</style>