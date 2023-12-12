<template>
    <a href="#" class="mb-7 group">
        <VideoItemThumbnail :index="index"></VideoItemThumbnail>
        <VideoItemInfo :index="index"></VideoItemInfo>
      </a>
</template>

<script>
import VideoItemThumbnail from './VideoItemThumbnail.vue'
import VideoItemInfo from './VideoItemInfo.vue'

export default {
  components: {VideoItemThumbnail, VideoItemInfo},
  props: ['index']

}


</script>