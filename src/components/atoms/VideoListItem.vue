<template>
  <li
    class="app-videoListItem list-group-item media"
    @click="onVideoSelect"
  >
    <img class="mr-3" :src="thumbnailUrl" alt="" />
    <div class="media-body">
      {{ video.snippet.title }}
    </div>
  </li>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: {
    video: {
      type: Object
    }
  },
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoSelect() {
      this.$emit('videoSelect', this.video);
    }
  }
};
</script>
