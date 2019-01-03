<template>
  <li class="list-group-item">
    <img :src="thumbnail" />
    {{ video.snippet.title }}
  </li>
</template>

<script>
  export default {
    name: 'VideoListItem',
    props: {
      video: Object
    },
    computed: {
      thumbnail() {
        return this.video.snippet.thumbnails.default.url;
      }
    }
  };
</script>
