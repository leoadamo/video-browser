<template>
  <div>
    <SearchBar @termChange="onTermChange" />
    <VideoList :data="videos" />
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from '@/components/atoms/SearchBar';
import VideoList from '@/components/molecules/VideoList';

export default {
  name: 'App',
  data() {
    return {
      videos: []
    };
  },
  components: {
    SearchBar,
    VideoList
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: process.env.VUE_APP_API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm
          }
        })
        .then(({ data }) => (this.videos = data.items));
    }
  }
};
</script>

<style></style>
