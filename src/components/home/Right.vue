<script setup>
const floorList = ['一楼', '二楼', '三楼', '四楼', '五楼']
</script>

<template>
  <div class="todayRightBox">
    <img class="todayRightBG" src="../../assets/img/common/homeRightBG.png" alt="" />
  </div>
</template>

<style lang="less" scoped>
.todayRightBox {
  flex: 1;
  display: flex;
  align-items: center;
  .todayRightBG {
    width: calc(1067px * 0.85);
    height: calc(777px * 0.85);
    object-fit: contain;
  }
}
</style>
