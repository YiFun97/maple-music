<template>
  <div class="slider" ref="slider">
    <div class="slider-group" ref="sliderGroup">
      <slot>
      </slot>
    </div>
    <!-- <div class="dots">
      <span class="dot" :class="{active: currentPageIndex === index }" v-for="(item, index) in dots" :key="item"></span>
    </div> -->
  </div>
</template>

<script type="text/ecmascript-6">
  import {addClass} from '../../common/js/dom'
  import bScroll from 'better-scroll'

  export default {
    name: 'slider',
    props:{
        loop: {
            type:Boolean,
            default: true
        },
        autoPlay:{
            type: Boolean,
            default:true
        },
        interval: {
            type: Number,
            default: 4000
        }
    },
    mounted() {
        setTimeout(()=>{
            console.log('slider mounted')
            this.setSliderWidth()
            this.initSlider()
        }, 20)
    },
    methods:{
      setSliderWidth() {
          console.log('444444')
          this.children = this.$refs.sliderGroup.children

          let width = 0
          let sliderWidth = this.$refs.slider.clientWidth //拿到容器的宽度
          
          for(let i = 0; i < this.children.length; i++){
              let child = this.children[i]
              addClass(child, 'slider-item')

              child.style.width = sliderWidth + 'px'
              width += sliderWidth
          }

          if (this.loop) {
              width += 2 * sliderWidth
          }
          this.$refs.sliderGroup.style.width = width + 'px'
      },
      initSlider() {
          this.slider = new bScroll(this.$refs.slider, {
            scrollX: true,
            scrollY: false,
            momentum: false,
            snap: {
                loop: this.loop,
                threshold: 0.3,
                speed: 400
            } 
          })
      }
    }
  }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  @import "~common/stylus/variable"

  .slider
    min-height: 1px
    .slider-group
      position: relative
      overflow: hidden
      white-space: nowrap
      .slider-item
        float: left
        box-sizing: border-box
        overflow: hidden
        text-align: center
        a
          display: block
          width: 100%
          overflow: hidden
          text-decoration: none
        img
          display: block
          width: 100%
    .dots
      position: absolute
      right: 0
      left: 0
      bottom: 12px
      text-align: center
      font-size: 0
      .dot
        display: inline-block
        margin: 0 4px
        width: 8px
        height: 8px
        border-radius: 50%
        background: $color-text-l
        &.active
          width: 20px
          border-radius: 5px
          background: $color-text-ll
</style>