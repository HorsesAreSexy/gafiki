<template>
  <div class="switch">
    <div
      v-for="(name, index) in ['Агась','Ноуп']"
      :key="index"
      class="case"
      :class="chosen === index ? 'chosen' : ''"
      @click="$emit('swap', chosen = index)"
    >
      {{ name }}
    </div>
  </div>
</template>
<script>
export default {
  name: 'BodyGraphSwap',
  data () {
    return {
      chosen: 0
    }
  }
}
</script>

<style scoped lang="stylus">
    .switch
        border 2px solid black
        border-radius 50px
        background white
        position relative
        top 5px
        display inline-block
        margin-left 50%
        transform translate(-50%)
        .case
            display inline-block
            padding 16px 12px
            position relative
            font-size 18px
            font-weight bold
            cursor pointer
            &:not(.chosen):hover
                text-decoration underline
            &:last-of-type
                margin-right 0
            &.chosen
                cursor default
                background black
                margin -10px
                padding-top 26px
                padding-bottom @padding-top
                color white
                &:nth-child(1)
                    margin-right 0
                    border-radius 50px 0 0 50px
                &:nth-child(2)
                    margin-left 0
                    border-radius 0 50px 50px 0
</style>
