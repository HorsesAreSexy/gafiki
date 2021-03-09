<template>
  <div class="selected">
    <div class="field" :style="`left: calc(-${100 * type}% - ${type * '100'}px);`">
      <slot name="graph" />
    </div>
    <div class="panel">
      <div class="line">
        <div class="desc">
          График:
        </div>
        <div class="content title">
          <slot name="name" />
        </div>
      </div>
      <div class="line">
        <div class="desc">
          Типаж:
        </div>
        <slot name="select" />
      </div>
      <div class="line">
        <div class="desc">
          Показывать ли значения точек?
        </div>
        <slot name="swap" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BodyGraphContainer',
  props: {
    type: {
      type: Number,
      default: 0
    }
  }
}
</script>

<style scoped lang="stylus">
    .selected
        height 100%
        overflow hidden
        panelHeight = 300px
        .field
          height 100%
          margin-bottom panelHeight * -1
          padding-bottom panelHeight
          white-space nowrap
          position relative
          transition left 0.4s
          .instance
            display inline-block
            margin-left 100px
            height 100%
            width 100%
            box-sizing content-box
            &:first-of-type
              margin-left 0
        .panel
          position absolute
          bottom 0
          left 0
          width 100%
          height panelHeight
          display flex
          flex-direction column
          justify-content space-around
          .line
            position relative
            &:before
              content ''
              position absolute
              top 50%
              left 0
              height 2px
              width 100%
              background black
              margin-top (-@height / 2 + 5px)
            .desc
              position absolute
              top 50%
              left 0
              font-size 16px
              transform translateY(-50%)
              background white
              padding-right 10px
            .content
              display inline-block
              margin-left 50%
              transform translate(-50%)
              &.title
                font-size 30px
                font-weight bold
                background white
                padding 0 20px
</style>
