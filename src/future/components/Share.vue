<template>
  <section class="share">
    <div class="share__fb-like-wrapper">
      <div class="fb-like" data-href="https://udn.com/upf/newmedia/2018_data/cloudgate/future.html" data-layout="button_count" data-action="like" data-size="small" data-show-faces="true" data-share="true"></div>
    </div>
    <div @click="lineShare">
      <img class="line-share" src="//media.line.me/img/button/zh-hant/84x20.png" alt="LINE分享給朋友" width="84" height="20">
    </div>
  </section>
</template>

<script>
import { detectPlatform, detectMob } from 'udn-newmedia-utils';

export default {
  name: 'Share',
  methods: {
    lineShare() {
      window.ga('send', {
        hitType: 'event',
        eventCategory: 'Line Share',
        eventAction: 'click',
        eventLabel: `[${detectPlatform()}] [${document.querySelector('title').innerHTML}] [line share]`,
      });
      if (detectMob()) {
        window.open(`//line.me/R/msg/text/?${document.querySelector('title').innerHTML}%0D%0A%0D%0A${document.querySelector('meta[property="og:description"]').content}%0D%0A%0D%0Ahttps://udn.com/upf/newmedia/2018_data/cloudgate/future.html`);
      } else {
        window.open('https://lineit.line.me/share/ui?url=https://udn.com/upf/newmedia/2018_data/cloudgate/future.html');
      }
    },
  },
};
</script>

<style lang="scss">
.share {
  display: flex;
  height: 20px;
  // margin-bottom: 48px;
  &__fb-like-wrapper {
    margin-right: 8px;
  }
  // &__button {
  //   cursor: pointer;
  // }
}
.fb-like, .line-share {
  cursor: pointer;
}
</style>

