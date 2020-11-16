<template>
  <div class="rank" ref='rank'>
    排行页面
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    data() {
      return {
        topList:[]
      }
    },
    created() {
    },
    components:{
    },
    methods:{
    }
  }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  .rank
    position :fixed
    width :100%
    top: 88px
    bottom :0
    .toplist
      height: 100%
      overflow hidden
      .item
        display :flex
        margin :0 20px
        padding-top :20px
        height :100px
        &:last-child
          padding-bottom:20px
        .icon
          flex 0 0 100px
          width 100px
          height 100px  
        .songlist
          flex 1
          display flex
          flex-direction column
          justify-content center
          padding 0 20px
          height 100px
          background #333333
          overflow hidden
          .song
            font-size 12px
            color rgba(255,255,255,0.3)
            line-height 25px
            overflow: hidden;
            white-space: nowrap;
            text-overflow: ellipsis;
    .loading-container
        position: absolute
        width: 100%
        top: 50%
        transform: translateY(-50%)      
</style>