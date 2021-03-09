<template>
  <div class="container">
    <MenuContainer>
      <MenuItem
        v-for="(data, index) in dataChart"
        :key="index"
        :active="activeOption === index"
        @click="activeOption = index"
      >
        {{ data.name }}
      </MenuItem>
    </MenuContainer>
    <BodyContainer>
      <BodyPlaceholder v-if="activeOption === null" />
      <BodyGraphContainer v-else :type="type">
        <template #graph>
          <G2Graph
            v-for="(graphType,index) in ['line','step','column']"
            :key="index"
            :graph-data="dataChart[activeOption].graph"
            :graph-type="graphType"
            :graph-order="index"
            :setting-dots="dots"
            class="instance"
            :style="`left: ${100 * index}%;`"
          />
        </template>
        <template #name>
          {{ dataChart[activeOption].name }}
        </template>
        <template #select>
          <BodyGraphSelect @change="index => type = index" />
        </template>
        <template #swap>
          <BodyGraphSwap @swap="index => dots = index" />
        </template>
      </BodyGraphContainer>
    </BodyContainer>
  </div>
</template>

<script>
import dataChart from 'static/dataChart.json'
export default {
  data () {
    return {
      dataChart,
      activeOption: null,
      type: 0,
      dots: 0
    }
  }
}
</script>

<style scoped lang="stylus">
  .container
    position absolute
    top 0
    left 0
    width 100%
    height 100%
    menuWidth = 250px
    linesWidth = 12px
    gridX = 15px
    gridY = 20px
    >*
      float left
</style>
