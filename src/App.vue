<script setup>
import { ref, reactive, onMounted, onBeforeUnmount } from 'vue'
import { RouterView, useRouter } from 'vue-router'
import { formatDate } from './hook/getTime'

const router = useRouter()
let btnItemActive = ref(1)
let list = reactive([
  {
    id: 1,
    name: '首页',
    route: '/',
    BGUrl: './assets/img/header1.png',
  },
  {
    id: 2,
    name: '今日统计人数',
    route: '/today',
    BGUrl: './assets/img/header2.png',
  },
  {
    id: 3,
    name: '历史统计人数',
    route: '/history',
    BGUrl: './assets/img/header3.png',
  },
  {
    id: 4,
    name: '用户管理',
    route: '/4',
  },
  {
    id: 5,
    name: '权限管理',
    route: '/5',
  },
  {
    id: 6,
    name: '接入管理',
    route: '/6',
  },
])
let nowYear = ref('')
let nowDay = ref('')

const btnClick = (item) => {
  router.replace(item.route)
  btnItemActive.value = item.id
}
const btnStyle = (item) => {
  return item.id === btnItemActive.value ? 'btnItem btnItemActive' : 'btnItem'
}
const timeStart = () => {
  nowYear.value = formatDate(new Date()).nowYear
  nowDay.value = formatDate(new Date()).nowDay
  setInterval(() => {
    nowYear.value = formatDate(new Date()).nowYear
    nowDay.value = formatDate(new Date()).nowDay
  }, 1000)
}

onMounted(() => {
  timeStart()
  if (window.location.pathname === '/') {
    btnItemActive.value = 1
  } else if (window.location.pathname.indexOf('/today') != -1) {
    btnItemActive.value = 2
  } else if (window.location.pathname.indexOf('/history') != -1) {
    btnItemActive.value = 3
  } else {
    btnItemActive.value = 0
  }
})
</script>

<template>
  <div class="view">
    <img class="leftBG" src="./assets/img/base/leftBG.png" alt="" />
    <img class="rightBG" src="./assets/img/base/leftBG.png" alt="" />
    <img class="bottomBG" src="./assets/img/base/bottomBG.png" alt="" />
    <div class="header">
      <div class="timeBox">
        <p class="time">{{ nowYear }}</p>
      </div>
      <div class="btnLeftBox">
        <div v-for="(item, index) in list.slice(0, 1)" :class="btnStyle(item)">
          <p class="btnText" @click="btnClick(item)">{{ item.name }}</p>
        </div>
        <div v-for="(item, index) in list.slice(1, 3)" :class="btnStyle(item)">
          <p class="btnText" @click="btnClick(item)">{{ item.name }}</p>
        </div>
      </div>
      <div class="headerContent">
        <p class="headerContentTitle1">辽宁诚仕达人数统计平台</p>
        <p class="headerContentTitle2">Chengshida Personnel Statistics Platform</p>
      </div>
      <div class="btnRightBox">
        <div v-for="(item, index) in list.slice(3, 6).reverse()" :class="btnStyle(item)">
          <p class="btnText" @click="btnClick(item)">{{ item.name }}</p>
        </div>
      </div>
      <div class="timeBox">
        <p class="time">{{ nowDay }}</p>
      </div>
    </div>
    <div class="main">
      <RouterView />
    </div>
  </div>
</template>

<style lang="less" scoped>
.view {
  width: 100vw;
  height: 100vh;
  .leftBG {
    width: 24px;
    height: 849px;
    object-fit: contain;
    position: absolute;
    top: 50%;
    left: 0;
    transform: translate(0, -50%);
  }
  .rightBG {
    width: 24px;
    height: 849px;
    object-fit: contain;
    position: absolute;
    top: 42%;
    right: 0;
    transform: translate(0, -50%) rotate(180deg);
  }
  .bottomBG {
    width: 100%;
    height: 50px;
    object-fit: contain;
    position: absolute;
    left: 0;
    bottom: 0;
  }
  .header {
    width: 100%;
    height: 77px;
    background-image: url('./assets/img/base/header.png');
    background-size: 100% 100%;
    background-repeat: no-repeat;
    display: flex;
    justify-content: space-between;
    .timeBox {
      width: 104px;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      .time {
        font-size: 16px;
        font-weight: 500;
        color: #c8e7ff;
        margin-top: 8px;
      }
    }
    .headerContent {
      width: 710px;
      height: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      .headerContentTitle1 {
        font-size: 40px;
        font-family: YouSheBiaoTiHei-Regular, YouSheBiaoTiHei;
        font-weight: 700;
        line-height: 54px;
        letter-spacing: 8px;
        // text-shadow: 0px 5px 1px #040f18;
        background: linear-gradient(
          180deg,
          #d1eafc 0%,
          #dcedfb 33%,
          #e4f7ff 53%,
          #aacfe5 53%,
          #e9f4fa 74%
        );
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
      }
      .headerContentTitle2 {
        margin-top: 5px;
        font-size: 10px;
        font-family: Source Han Sans CN-Medium, Source Han Sans CN;
        font-weight: 500;
        color: #6fa7c8;
        letter-spacing: 2px;
        -webkit-background-clip: text;
      }
    }

    .btnItem {
      width: 136px;
      height: 100%;
      position: relative;
      display: flex;
      align-items: center;
      justify-content: center;
      .btnText {
        cursor: pointer;
        margin-bottom: 16px;
        font-size: 20px;
        font-family: YouSheBiaoTiHei-Regular, YouSheBiaoTiHei;
        font-weight: 600;
        letter-spacing: 2px;
        background: linear-gradient(180deg, #77bcf2 0%, #e3f4ff 45%, #77bcf2 65%, #a9d7ff 85%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
      }
    }
    .btnItemActive {
      .btnText {
        background: linear-gradient(180deg, #ffea95 0%, #fff6e4 45%, #fec302 65%, #fbf5e2 75%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        &::after {
          content: '';
          position: absolute;
          width: 105px;
          height: 39px;
          top: 2px;
          left: 50%;
          transform: translate(-50%, 0);
          background-image: url('./assets/img/base/highLight.png');
          background-size: contain;
        }
      }
      &::after {
        content: '';
        position: absolute;
        width: 27px;
        height: 15px;
        top: 56px;
        left: 50%;
        transform: translate(-50%, 0);
        background-image: url('./assets/img/base/hand.png');
        background-size: contain;
      }
    }
    .btnLeftBox {
      flex: 1;
      display: flex;
      padding: 0 12px;
      justify-content: space-between;
      align-items: center;
    }
    .btnRightBox {
      flex: 1;
      display: flex;
      padding: 0 30px 0 0;
      justify-content: space-between;
      align-items: center;
    }
  }
  .main {
    width: 100%;
    height: calc(100vh - 77px);
  }
}
</style>
