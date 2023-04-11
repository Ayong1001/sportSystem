<script setup>
import * as echarts from 'echarts'
import { ref, onMounted } from 'vue'

let isPieBtn = ref(false)
let isBarBtn = ref(false)

let myChartOption1 = {
  title: {
    show: true,
    text: 1021,
    subtext: '总人数',
    top: 'center',
    left: 'center',
    textStyle: {
      color: '#fff',
      fontSize: 26,
    },
    subtextStyle: {
      color: '#fff',
      fontSize: 13,
    },
    itemGap: 5,
  },
  xAxis: { show: false },
  yAxis: {
    show: false,
  },
  tooltip: {
    trigger: 'item',
  },
  emptyCircleStyle: {
    color: '#E6E6E6',
  },
  series: [
    {
      name: '',
      type: 'pie',
      radius: ['65%', '80%'],
      startAngle: 300,
      avoidLabelOverlap: false,
      itemStyle: {
        borderRadius: 30,
      },
      data: [
        { value: 800, name: '男性人数' },
        { value: 221, name: '女性人数' },
      ],
      color: ['#4A8DF0', '#E6E6E6'],
      label: {
        formatter: '{c|{c}} \n {b|{b}}',
        rich: {
          c: {
            color: '#4A8DF0',
            fontSize: 26,
          },
          b: {
            color: '#B8BECD',
            fontSize: 13,
          },
        },
        distanceToLabelLine: 32,
      },
      labelLine: {
        length: 30,
        length2: 20,
        lineStyle: {
          color: '#4E5969',
          width: 2,
          type: 'dashed',
          join: 'round',
        },
      },
      labelLayout: {
        align: 'center',
      },
    },
  ],
}
let myChartOption2 = {
  title: { show: false },
  xAxis: {
    show: true,
    type: 'category',
    offset: 5,
    data: ['0-18岁', '19-35岁', '36-45岁', '46-65岁', '65岁以上'],
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
    show: true,
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
      data: [182, 311, 271, 148, 109],
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
      emphasis: {
        label: {
          show: true,
          color: '#fff',
          fontSize: 20,
          position: 'top',
        },
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
    },
  ],
}
let myChartOption3 = {
  title: { show: false },
  xAxis: {
    show: true,
    type: 'category',
    offset: 5,
    data: ['男性人数', '女性人数'],
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
    show: true,
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
      data: [800, 221],
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
      emphasis: {
        label: {
          show: true,
          color: '#fff',
          fontSize: 20,
          position: 'top',
        },
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
    },
  ],
}
let myChartOption4 = {
  title: {
    show: true,
    text: 1021,
    subtext: '总人数',
    top: 'center',
    left: 'center',
    textStyle: {
      color: '#fff',
      fontSize: 26,
    },
    subtextStyle: {
      color: '#fff',
      fontSize: 13,
    },
    itemGap: 5,
  },
  xAxis: { show: false },
  yAxis: {
    show: false,
  },
  tooltip: {
    trigger: 'item',
  },
  emptyCircleStyle: {
    color: '#E6E6E6',
  },
  series: [
    {
      name: '',
      type: 'pie',
      radius: ['45%', '60%'],
      startAngle: 300,
      avoidLabelOverlap: false,
      itemStyle: {
        borderRadius: 30,
      },
      data: [
        { value: 182, name: '0-18岁' },
        { value: 311, name: '19-35岁' },
        { value: 271, name: '36-45岁' },
        { value: 148, name: '46-65岁' },
        { value: 109, name: '65岁以上' },
      ],
      color: [
        '#4A8DF0',
        '#E6E6E6',
        '#fac858',
        '#ee6666',
        '#73c0de',
        '#3ba272',
        '#fc8452',
        '#9a60b4',
        '#ea7ccc',
      ],
      label: {
        formatter: '{c|{c}} \n {b|{b}}',
        rich: {
          c: {
            color: '#4A8DF0',
            fontSize: 26,
          },
          b: {
            color: '#B8BECD',
            fontSize: 13,
          },
        },
        distanceToLabelLine: 32,
      },
      labelLine: {
        length: 25,
        length2: 15,
        lineStyle: {
          color: '#4E5969',
          width: 2,
          type: 'dashed',
          join: 'round',
        },
      },
      labelLayout: {
        align: 'center',
      },
    },
  ],
}
const todayBtn1 = () => {
  echarts.init(document.getElementById('todayPie')).setOption(myChartOption3)
  isPieBtn.value = !isPieBtn.value
}
const todayBtn2 = () => {
  echarts.init(document.getElementById('todayBar')).setOption(myChartOption2)
  isBarBtn.value = !isBarBtn.value
}

onMounted(() => {
  echarts.init(document.getElementById('todayPie')).setOption(myChartOption1)
  echarts.init(document.getElementById('todayBar')).setOption(myChartOption2)
})
</script>

<template>
  <div class="mainLift">
    <div class="mainLiftTop">
      <div class="title">
        <img class="leftTip" src="../../assets/img/today/todaySexBG.png" alt="" />
        <img
          class="rightChange"
          @click="todayBtn1()"
          src="../../assets/img/common/change.png"
          alt=""
        />
      </div>
      <div class="todayPieBox">
        <div id="todayPie"></div>
      </div>
    </div>
    <div class="mainLiftButtom">
      <div class="title">
        <img class="leftTip" src="../../assets/img/today/todayAgeBG.png" alt="" />
        <img
          class="rightChange"
          @click="todayBtn2()"
          src="../../assets/img/common/change.png"
          alt=""
        />
      </div>
      <div class="todayBarBox">
        <div id="todayBar"></div>
      </div>
    </div>
  </div>
</template>

<style lang="less" scoped>
.mainLift {
  width: 672px;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  .title {
    margin-bottom: 10px;
    display: flex;
    justify-content: space-between;
    .leftTip {
      width: 223px;
      height: 27px;
      object-fit: contain;
    }
    .rightChange {
      width: 20px;
      height: 20px;
      cursor: pointer;
      object-fit: contain;
    }
  }

  .mainLiftTop {
    width: 500px;
    height: 293px;
    margin: 20px;
    padding: 16px;
    background-image: url('../../assets/img/common/mainLiftTop.png');
    background-size: 100% 100%;
    background-repeat: no-repeat;
    .todayPieBox {
      width: 100%;
      height: 100%;
      #todayPie {
        width: 80%;
        height: 80%;
        margin: auto;
      }
      #todayPieToBar {
        width: 90%;
        height: 90%;
        margin: auto;
      }
    }
    // .todayPieBox1 {
    //   width: 100%;
    //   height: 100%;
    //   #todayPieToBar {
    //     width: 90%;
    //     height: 90%;
    //     margin: auto;
    //   }
    // }
  }
  .mainLiftButtom {
    width: 500px;
    height: 332px;
    margin: 20px;
    padding: 16px;
    background-image: url('../../assets/img/common/mainLiftButtom.png');
    background-size: 100% 100%;
    background-repeat: no-repeat;
    .todayBarBox {
      width: 100%;
      height: 100%;
      #todayBar {
        width: 90%;
        height: 90%;
        margin: auto;
      }
      #todayBarToPie {
        width: 80%;
        height: 80%;
        margin: auto;
      }
    }
  }
}
</style>
