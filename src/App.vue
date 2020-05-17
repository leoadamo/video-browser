<template>
  <div class="container">
    <SearchBar @termChange="onTermChange" />
    <div class="row">
      <VideoDetail :video="selectedVideo" />
      <VideoList :videos="videos" @videoSelect="onVideoSelect" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from '@/components/atoms/SearchBar';
import VideoList from '@/components/molecules/VideoList';
import VideoDetail from '@/components/molecules/VideoDetail';

export default {
  name: 'App',
  data() {
    return {
      videos: [],
      selectedVideo: null
    };
  },
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get(process.env.VUE_APP_API_URL, {
          params: {
            key: process.env.VUE_APP_API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm
          }
        })
        .then(({ data }) => (this.videos = data.items));
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    }
  }
};
</script>
