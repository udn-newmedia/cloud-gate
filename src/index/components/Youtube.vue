<template>
  <section class="youtube" :style="{ 'padding-bottom': aspectRatio }">
    <iframe class="youtube__player" :id="youtubeRef" :src="`https://www.youtube.com/embed/${youtubeId}?enablejsapi=1&modestbranding=1&rel=0&showinfo=0&iv_load_policy=3&playsinline=1&loop=1&origin=https://udn.com`" frameborder="0" allowfullscreen></iframe>
    <!-- <iframe class="youtube__player" :id="youtubeRef" :src="`https://www.youtube.com/embed/${youtubeId}?enablejsapi=1&modestbranding=1&rel=0&showinfo=0&iv_load_policy=3&playsinline=1&loop=1`" frameborder="0" allowfullscreen></iframe> -->
  </section>
</template>

<script>
export default {
  name: 'Youtube',
  props: ['youtubeId', 'youtubeRef'],
  computed: {
    aspectRatio() {
      if (this.$root.isMobileSize) return `${(this.$root.windowHeight / this.$root.windowWidth) * 100}%`;
      return 0;
    },
  },
};
</script>

<style lang="scss">
.youtube {
  position: relative;
  @media screen and (min-width: 576px) {
    height: 100vh;
  }
  &__player {
    width: 100%;
    height: 100%;
    position: absolute;
  }
}
</style>

