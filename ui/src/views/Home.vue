<template>
  <div class="home">
    <div v-if="loading" class="ui active centered inline loader" />
    <video-grid :values="videos" />
  </div>
</template>

<script>
import VideoGrid from '@/components/Video/VideoGrid.vue';

export default {
  name: 'home',
  components: {
    VideoGrid,
  },
  data() {
    return {
      videos: [],
      loading: true,
    };
  },
  metaInfo: {
    title: 'Home',
  },
  mounted() {
    this.$store.dispatch('tagged', { tags: 'home' }).then((videos) => {
      this.videos = videos;
      this.loading = false;
    });
  },
};
</script>
