<script setup>
import TodayLeft from '../components/today/Left.vue'
import TodayRight from '../components/today/Right.vue'
</script>

<template>
  <div class="today">
    <TodayLeft></TodayLeft>
    <TodayRight></TodayRight>
  </div>
</template>

<style lang="less" scoped>
.today {
  width: 100%;
  height: 100%;
  padding: 0 34px 50px 34px;
  display: flex;
}
</style>
