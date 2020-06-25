<template>
  <div class="">
    <div class="row">
      <div class="div-col-md-10">
        <p class="mb-3">Title: {{ videodetail.title }}</p>

        <p>Description: {{ videodetail.description }}</p>

        <p>Rating: {{ videodetail.rating_average }}</p>

        <p>Comments: {{ videodetail.list_comments }}</p>
        <p>URL: {{ videodetail.url }}</p>
        <p>Category: {{ videodetail.category }}</p>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";

export default {
  name: "VideoDetails",
  components: {},
  props: {
    videodetail: {}
  },
  data() {
    return {};
  },
  methods: {}
};
</script>

<style scoped></style>
