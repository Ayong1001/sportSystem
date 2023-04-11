<script setup>
import { ref } from 'vue'

const floorList = ['一楼', '二楼', '三楼', '四楼', '五楼']
const floorItemActive = ref(0)
const floorItemStyle = (index) => {
  return index === floorItemActive.value ? 'floorItem floorItemActive' : 'floorItem'
}
const floorItemClick = (index) => {
  floorItemActive.value = index
}
</script>

<template>
  <div class="todayRightBox">
    <img class="todayRightBG" src="../../assets/img/common/homeRightBG.png" alt="" />
    <div class="floorBox">
      <div
        v-for="(item, index) in floorList"
        @click="floorItemClick(index)"
        :class="floorItemStyle(index)"
      >
        <p class="floorItemText">{{ item }}</p>
      </div>
    </div>
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
  .floorBox {
    margin-left: 50px;
    margin-top: 380px;
    .floorItem {
      width: 142px;
      height: 52px;
      background-image: url('../../assets/img/common/btnBG.png');
      background-size: 100% 100%;
      background-repeat: no-repeat;
      display: flex;
      align-items: center;
      justify-content: center;
      .floorItemText {
        cursor: pointer;
        font-size: 18px;
        font-weight: 400;
        color: #ffffff;
      }
    }
    .floorItemActive {
      .floorItemText {
        color: #44cfffff;
      }
    }
  }
}
</style>
