<template>
  <div>
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList :videos="videos"></VideoList>
  </div>
</template>

<script>
  import SearchBar from './components/SearchBar';
  import VideoList from './components/VideoList';
  import axios from 'axios';
  const API_KEY = 'AIzaSyCCKFqDgJOfmrCXDGxmkp_LWuJ92YGk9LM';

  export default {
    name: 'App',
    components: {
      SearchBar,
      VideoList
    },
    data() {
      return {
        videos: []
      };
    },
    methods: {
      onTermChange(newTerm) {
        axios.get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: newTerm
          }
        }).then(response => this.videos = response.data.items);
      }
    }
  };
</script>