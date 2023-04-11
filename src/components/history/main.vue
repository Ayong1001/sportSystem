<script setup>
import * as echarts from 'echarts'
import { ref, reactive, onMounted } from 'vue'

let tableItemActive = ref(0)
let dropdownActive = ref(false)
let dataType = ref('按年龄')

const tableItemStyle = (index) => {
  return index === tableItemActive.value ? 'tableItem tableItemActive' : 'tableItem'
}
const ageList = [
  { id: 1, text: '0-18岁' },
  { id: 2, text: '19-35岁' },
]
const barList = reactive([
  {
    id: 'day',
    dataX: [
      '03-23',
      '03-24',
      '03-25',
      '03-26',
      '03-27',
      '03-28',
      '03-29',
      '03-30',
      '03-31',
      '04-01',
      '04-02',
      '04-03',
    ],
    dataY1: [78, 76, 71, 80, 75, 86, 82, 73, 80, 76, 79, 77],
    dataY2: [58, 66, 68, 71, 70, 61, 72, 63, 68, 62, 71, 68],
  },
  {
    id: 'moon',
    dataX: [
      '03-23',
      '03-24',
      '03-25',
      '03-26',
      '03-27',
      '03-28',
      '03-29',
      '03-30',
      '03-31',
      '04-01',
      '04-02',
      '04-03',
    ],
    dataY1: [78, 76, 71, 80, 75, 86, 82, 73, 80, 76, 79, 77],
    dataY2: [58, 66, 68, 71, 70, 61, 72, 63, 68, 62, 71, 68],
  },
  {
    id: 'week',
    dataX: [
      '03-23',
      '03-24',
      '03-25',
      '03-26',
      '03-27',
      '03-28',
      '03-29',
      '03-30',
      '03-31',
      '04-01',
    ],
    dataY1: [78, 71, 80, 75, 82, 73, 80, 76, 79, 77],
    dataY2: [58, 66, 68, 70, 61, 72, 63, 68, 62, 71],
  },
  {
    id: 'quarter',
    dataX: ['03-23', '03-24', '03-25', '03-26'],
    dataY1: [80, 73, 80, 79],
    dataY2: [58, 70, 61, 63],
  },
  {
    id: 'year',
    dataX: ['03-23', '03-24', '03-25', '03-26', '03-27'],
    dataY1: [71, 80, 86, 73, 80],
    dataY2: [58, 68, 71, 72, 62],
  },
])
const barListAge1 = reactive([
  {
    id: 'day',
    dataX: [
      '03-23',
      '03-24',
      '03-25',
      '03-26',
      '03-27',
      '03-28',
      '03-29',
      '03-30',
      '03-31',
      '04-01',
      '04-02',
      '04-03',
    ],
    dataY1: [78, 76, 71, 80, 75, 86, 82, 73, 80, 76, 79, 77].sort(() => Math.random() - 0.5),
  },
  {
    id: 'moon',
    dataX: [
      '03-23',
      '03-24',
      '03-25',
      '03-26',
      '03-27',
      '03-28',
      '03-29',
      '03-30',
      '03-31',
      '04-01',
      '04-02',
      '04-03',
    ],
    dataY1: [78, 76, 71, 80, 75, 86, 82, 73, 80, 76, 79, 77].sort(() => Math.random() - 0.5),
  },
  {
    id: 'week',
    dataX: [
      '03-23',
      '03-24',
      '03-25',
      '03-26',
      '03-27',
      '03-28',
      '03-29',
      '03-30',
      '03-31',
      '04-01',
    ],
    dataY1: [78, 71, 80, 75, 82, 73, 80, 76, 79, 77].sort(() => Math.random() - 0.5),
  },
  {
    id: 'quarter',
    dataX: ['03-23', '03-24', '03-25', '03-26'],
    dataY1: [80, 73, 80, 79].sort(() => Math.random() - 0.5),
  },
  {
    id: 'year',
    dataX: ['03-23', '03-24', '03-25', '03-26', '03-27'],
    dataY1: [71, 80, 86, 73, 80].sort(() => Math.random() - 0.5),
  },
])
const barListAge2 = reactive([
  {
    id: 'day',
    dataX: [
      '03-23',
      '03-24',
      '03-25',
      '03-26',
      '03-27',
      '03-28',
      '03-29',
      '03-30',
      '03-31',
      '04-01',
      '04-02',
      '04-03',
    ],
    dataY1: [78, 76, 71, 80, 75, 86, 82, 73, 80, 76, 79, 77].sort(() => Math.random() - 0.5),
  },
  {
    id: 'moon',
    dataX: [
      '03-23',
      '03-24',
      '03-25',
      '03-26',
      '03-27',
      '03-28',
      '03-29',
      '03-30',
      '03-31',
      '04-01',
      '04-02',
      '04-03',
    ],
    dataY1: [78, 76, 71, 80, 75, 86, 82, 73, 80, 76, 79, 77].sort(() => Math.random() - 0.5),
  },
  {
    id: 'week',
    dataX: [
      '03-23',
      '03-24',
      '03-25',
      '03-26',
      '03-27',
      '03-28',
      '03-29',
      '03-30',
      '03-31',
      '04-01',
    ],
    dataY1: [78, 71, 80, 75, 82, 73, 80, 76, 79, 77].sort(() => Math.random() - 0.5),
  },
  {
    id: 'quarter',
    dataX: ['03-23', '03-24', '03-25', '03-26'],
    dataY1: [80, 73, 80, 79].sort(() => Math.random() - 0.5),
  },
  {
    id: 'year',
    dataX: ['03-23', '03-24', '03-25', '03-26', '03-27'],
    dataY1: [71, 80, 86, 73, 80].sort(() => Math.random() - 0.5),
  },
])
const imgList = [
  { imgUrl: new URL('../../assets/img/history/day.png', import.meta.url).href },
  { imgUrl: new URL('../../assets/img/history/moon.png', import.meta.url).href },
  { imgUrl: new URL('../../assets/img/history/week.png', import.meta.url).href },
  { imgUrl: new URL('../../assets/img/history/quarter.png', import.meta.url).href },
  { imgUrl: new URL('../../assets/img/history/year.png', import.meta.url).href },
]
const myChartOption = (isLegend, dataX, dataY1, dataY2) => {
  return {
    legend: {
      show: isLegend,
      orient: 'vertical',
      data: ['男性', '女性'],
      right: 0,
      textStyle: {
        color: '#fff',
      },
    },
    tooltip: {
      trigger: 'axis',
      borderColor: '#98CFFAFF',
      backgroundColor: '#0000008F',
      textStyle: {
        color: '#fff',
        fontWeight: 'normal',
      },
    },
    xAxis: {
      type: 'category',
      offset: 5,
      data: dataX,
      axisLabel: {
        fontSize: 15,
        interval: 0,
      },
      axisTick: {
        show: false,
      },
      axisLine: {
        lineStyle: {
          width: 2,
          color: '#5C90A1',
        },
      },
    },
    yAxis: {
      type: 'value',
      offset: 5,
      name: '数量',
      nameLocation: 'end',
      nameGap: 25,
      nameTextStyle: {
        fontSize: 15,
        align: 'right',
      },
      axisLabel: {
        fontSize: 15,
      },
      splitLine: {
        lineStyle: {
          type: 'dashed',
          color: '#37535C',
        },
      },
    },
    barWidth: '15',
    series: [
      {
        type: 'bar',
        name: isLegend ? '男性' : '人数',
        data: dataY1,
        itemStyle: {
          color: {
            type: 'linear',
            x: 0,
            y: 0,
            x2: 0,
            y2: 1,
            colorStops: [
              {
                offset: 0,
                color: 'rgba(126, 224, 255)',
              },
              {
                offset: 1,
                color: 'rgba(126, 224, 255,0)',
              },
            ],
            global: false,
          },
        },
      },
      {
        type: 'bar',
        name: '女性',
        data: dataY2,
        itemStyle: {
          color: {
            type: 'linear',
            x: 0,
            y: 0,
            x2: 0,
            y2: 1,
            colorStops: [
              {
                offset: 0,
                color: 'rgba(255,226,87)',
              },
              {
                offset: 1,
                color: 'rgba(255,226,87,0)',
              },
            ],
            global: false,
          },
        },
      },
    ],
  }
}
const tableItemClick = (index) => {
  tableItemActive.value = index
  if (index === 0) {
    barList.forEach((item, index) => {
      echarts
        .init(document.getElementById(item.id))
        .setOption(myChartOption(true, item.dataX, item.dataY1, item.dataY2))
    })
  }
}
const dropdownOpen = () => {
  dropdownActive.value = !dropdownActive.value
}
const dropdownClose = () => {
  dropdownActive.value = false
}
const dropdownStyle = () => {
  return dropdownActive.value ? 'display: block;' : ''
}
const btnRevolve = () => {
  return !dropdownActive.value ? 'btnP' : 'btnP btnPD'
}
const dropdownClick = (item) => {
  dataType.value = item.text
  tableItemClick(1)
  if (item.id === 1) {
    barListAge1.forEach((item, index) => {
      echarts
        .init(document.getElementById(item.id))
        .setOption(myChartOption(false, item.dataX, item.dataY1))
    })
  } else if (item.id === 2) {
    barListAge2.forEach((item, index) => {
      echarts
        .init(document.getElementById(item.id))
        .setOption(myChartOption(false, item.dataX, item.dataY1))
    })
  }
  dropdownClose()
}
onMounted(() => {
  barList.forEach((item, index) => {
    echarts
      .init(document.getElementById(item.id))
      .setOption(myChartOption(true, item.dataX, item.dataY1, item.dataY2))
  })
  document.addEventListener('click', function () {
    dropdownClose()
  })
})
</script>

<template>
  <div class="tableBox">
    <div :class="tableItemStyle(0)" @click="tableItemClick(0)">
      <p class="tableItemText">按性别</p>
    </div>
    <div :class="tableItemStyle(1)" @click.stop="dropdownOpen()">
      <div :class="btnRevolve()"></div>
      <div class="dropdown">
        <p class="tableItemText">{{ dataType }}</p>
        <div class="dropdown-content" :style="dropdownStyle()">
          <p v-for="item in ageList" @click.stop="dropdownClick(item)">{{ item.text }}</p>
        </div>
      </div>
    </div>
  </div>
  <div class="barBox">
    <div class="barItem1" v-for="(item, index) in barList.slice(0, 2)">
      <img :src="imgList[index].imgUrl" alt="" />
      <div :id="item.id" class="echartsBar"></div>
    </div>
    <div class="barItem2" v-for="(item, index) in barList.slice(2, 5)">
      <img :src="imgList.slice(2, 5)[index].imgUrl" alt="" />
      <div :id="item.id" class="echartsBar"></div>
    </div>
  </div>
</template>

<style lang="less" scoped>
.tableBox {
  width: 100%;
  display: flex;
  .tableItem {
    width: 142px;
    height: 52px;
    cursor: pointer;
    margin-right: 32px;
    background-image: url('../../assets/img/common/btnBG.png');
    background-size: 100% 100%;
    background-repeat: no-repeat;
    display: flex;
    align-items: center;
    justify-content: center;
    .tableItemText {
      position: relative;
      font-size: 18px;
      font-weight: 400;
      color: #ffffff;
    }
    .btnP {
      position: absolute;
      top: 22px;
      right: 14px;
      border-top: 8px solid white;
      border-bottom: 8px solid transparent;
      border-left: 8px solid transparent;
      border-right: 8px solid transparent;
    }
    .btnPD {
      transform: rotate(180deg);
      top: 14px;
    }
  }
  .tableItemActive {
    .tableItemText {
      color: #44cfffff;
    }
  }

  .dropdown {
    position: relative;
    display: inline-block;
    .dropdown-content {
      display: none;
      position: absolute;
      z-index: 99;
      top: 30px;
      left: 50%;
      transform: translate(-50%, 0);
      background-color: #8383838f;
      border: 1px solid rgb(2, 20, 34);
      min-width: 128px;
      padding: 12px 16px;
      p {
        margin: auto;
        font-size: 18px;
        color: #ffffff;
        text-align: center;
        border-bottom: 1px solid #766f6f;
      }
      p ::active {
        color: #44cfffff;
      }
    }
  }
}
.barBox {
  width: 100%;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  img {
    width: 175px;
    height: 27px;
    object-fit: contain;
  }
  .echartsBar {
    width: 100%;
    height: 100%;
  }
  .barItem1 {
    width: 888px;
    height: 320px;
    margin-top: 32px;
    padding: 16px;
    background-image: url('../../assets/img/history/barItemBG1.png');
    background-size: cover;
  }
  .barItem2 {
    width: 580px;
    height: 320px;
    margin-top: 36px;
    padding: 16px;
    background-image: url('../../assets/img/history/barItemBG2.png');
    background-size: cover;
  }
}
</style>
