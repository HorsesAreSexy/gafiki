<template>
  <div class="space">
    <div class="wrap">
      <slot />
    </div>
  </div>
</template>

<script>
export default {
  name: 'BodyContainer'
}
</script>

<style scoped lang="stylus">
    .space
      padding 20px 15px
      padding-left 265px
      margin-left -250px
      height 100%
      width 100%
      .wrap
        position relative
        width 100%
        height 100%
</style>
