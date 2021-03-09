<template>
  <div class="menu">
    <div class="tip">
      ⇣ Выбери графиК ⇣
    </div>
    <slot />
  </div>
</template>

<script>
export default {
  name: 'MenuContainer'
}
</script>

<style scoped lang="stylus">
    .menu
      background white
      width 250px
      height 100%
      position relative
      z-index 2
      padding 10px 0
      padding-right 12px
      box-shadow 0 0 6px 0 black
      &:before
        content: ''
        position absolute
        top 0
        right 0
        width 12px
        height 100%
        border 0 solid black
        border-width 0 3px 0 2px
      .tip
        width 80%
        margin auto
        text-align center
        border-bottom 1px solid black
        padding-bottom 10px
        margin-bottom @padding-bottom
        font-size 18px
        font-weight bold
</style>
