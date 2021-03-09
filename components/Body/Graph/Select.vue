<template>
  <div class="select">
    <div
      v-for="(option, index) in ['line','step','column']"
      :key="index"
      class="option"
      :class="index === chosen ? 'chosen' : ''"
      @click="$emit('change', chosen = index)"
    >
      <div class="value">
        {{ option }}
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'BodyGraphSelect',
  data () {
    return {
      chosen: 0
    }
  }
}
</script>

<style scoped lang="stylus">
    .select
        display inline-block
        margin-left 50%
        transform translate(-50%)
        .option
            display inline-block
            padding 0 10px
            margin 0 10px
            position relative
            cursor pointer
            &:hover:before
                border-style dashed
            &.chosen
                background black
                color white
                cursor default
                border-radius 8px 8px 0 0
                &:before
                    background black
            &:before
                content ''
                position absolute
                bottom -4px
                left 0
                width 100%
                height 50%
                border 2px solid black
                border-top-width 0
                border-radius 0  0 8px 8px
                background white
            .value
                position relative
                font-size 22px
                font-weight bold
</style>
