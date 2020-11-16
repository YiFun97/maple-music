<template>
  <div class="singer" ref="singer">
  歌手页面
  </div>
</template>

<script type="text/ecmascript-6">

const HOT_NAME = '热门'
const HOT_SINGER_LEN = 10

  export default {
    data() {
      return {
        singers: []
      }
    },
    components:{
    },
    created() {
    },
    methods:{
    }
  }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
    .singer
      position: fixed
      top: 88px
      bottom: 0
      width: 100%
</style>
