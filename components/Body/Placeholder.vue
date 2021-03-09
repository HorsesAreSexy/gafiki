<template>
  <div class="placehold">
    <div class="center">
      <div class="title">
        GRAPH<span class="sub">ики</span>
        <span class="add">всякие</span>
      </div>
      <div class="art">
        <div class="pillar" />
        <div class="pillar" />
        <div class="pillar" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BodyPlaceholder'
}
</script>

<style scoped lang="stylus">
    .placehold
        top 50%
        transform translateY(-50%)
        position absolute
        text-align center
        width 100%
        .center
            display inline-block
            position relative
            .title
                font-size 200px
                font-weight bold
                position relative
                display inline-block
                .sub
                    vertical-align top
                    line-height 4
                    font-size 40px
                .add
                    transform rotate(60deg)
                    font-size 30px
                    font-weight normal
                    display inline-block
                    position absolute
                    bottom 86px
                    right -15px
            .art
                width 100%
                .pillar
                    background black
                    height 30px
                    box-shadow 0 0 2px 0 black
                    position relative
                    margin-bottom 14px
                    &:before
                        position absolute
                        right -50px
                        line-height @height
                        height 100%
                        font-size 40px
                    content = {
                    '🐎': 60,
                    '☭': 90,
                    '✡︎': 40
                    }
                    order = 1
                    for k in content
                        &:nth-child({order})
                            width unit(content[k], '%')
                            &:before
                                content k
                        order += 1
</style>
