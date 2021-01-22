<template>
  <div class="footer">
    <div class="footer--social-media">
      <img :src="discord"/>
      <img :src="ig"/>
      <img :src="yt"/>
    </div>
    <div class="footer--powered-by">
      Powered by Unity
    </div>
  </div>
</template>

<script>
import yt from '@/assets/yt.png';
import ig from '@/assets/ig.png';
import discord from '@/assets/discord.png';

export default {
  name: 'Footer.vue',
  props: {
    mousePos: {
      type: Object,
      default: () => ({}),
    },
  },
  data: () => ({
    yt,
    ig,
    discord,
  }),
};
</script>

<style lang="scss" scoped>
 .footer {
   display: flex;
   justify-content: space-between;
   position: fixed;
   align-items: center;
   width: 100%;
   bottom: 0;

   img {
     cursor: pointer;
   }

   &--social-media {
      display: flex;
      align-items: center;
      margin: 57px;
    }
   &--powered-by {
     align-self: flex-end;
     padding-bottom: 17px;
     padding-right: 31px;
     font-size: 13px;
     font-weight: 300;
   }
 }
</style>
