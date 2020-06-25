<template>
  <div class="">
    <div class="col-md-12 mb-5" v-if="createNew">
      <CreateVideo />
    </div>
    <div class="row">
      <div class="col-md-5 text-center nicefont">
        <h4>Welcome to the RatingVideoApp</h4>

        <button
          class="btn-sm btn-primary mb-3 btn-center"
          v-on:click="createdNew()"
        >
          Add video
        </button>

        <p v-for="video in videos" :key="video.id">
          {{ video.title }}
          <br />
          Rating: {{ video.rating_average }}

          <br />
          <br />
          <button
            class="btn-sm btn-primary mt-2 mb-3"
            v-on:click="videoDetail(video)"
          >
            Details
          </button>
        </p>
      </div>
      <div class="div-col-md-6">
        <VideoDetails v-bind:videodetail="videodetail" />
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";
import VideoDetails from "@/components/VideoDetails.vue";
import CreateVideo from "@/components/CreateVideo.vue";

export default {
  name: "home",
  components: {
    VideoDetails,
    CreateVideo
  },
  data() {
    return {
      videos: [],
      videodetail: Object,
      createNew: ""
    };
  },
  methods: {
    getVideos() {
      axios
        .get("http://127.0.0.1:8000/api/v1/videos")
        .then(res => (this.videos = res.data))
        .catch(err => console.log(err));
      console.log(this.videos);
    },
    videoDetail(video) {
      this.videodetail = video;
      console.log(this.videodetail);
    },
    createdNew() {
      this.createNew = !this.createNew;
    }
  },
  created() {
    this.getVideos();
    false;
  }
};
</script>

<style scoped>
.nicefont {
  @import url("https://fonts.googleapis.com/css2?family=Piedra&display=swap");

  font-size: 30px;
  font-family: "Piedra", cursive;
}
</style>
