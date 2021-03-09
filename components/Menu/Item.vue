<template>
  <div
    class="item"
    :class="active ? 'active' : ''"
    @click="$emit('click')"
  >
    <div class="text">
      <slot />
    </div>
  </div>
</template>

<script>
export default {
  name: 'MenuItem',
  props: {
    active: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style scoped lang="stylus">
    .item
        font-size 16px
        cursor pointer
        position relative
        height 43px
        .text
            padding 10px 15px
            white-space nowrap
            overflow hidden
            text-overflow ellipsis
            position relative
            border-bottom 2px solid white
        &.active
        &:hover
            .text
                border-bottom-color black
        &.active
            cursor default
            &:before
                content ''
                position absolute
                bottom 5px
                right -14px
                border 0 solid black
                border-width 2px 2px 0 0
                height 25px
                width @height
                transform rotate(45deg)
                background white
        &:not(&.active):hover .text
            display inline-block
            background white
            height 100%
            border-bottom-right-radius 4px
            &:before
                content ''
                position absolute
                top 0
                right 0
                width 'calc(100% - %s)' % 238px
                height 100%
                border 0 solid black
                border-width 2px 2px 0 0
                border-radius 0 4px 4px 0
</style>
