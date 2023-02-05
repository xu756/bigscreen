<template>
  <div class="content">
    <span class="title">设备详细</span>
    <span class="angle1"></span>
    <span class="angle2"></span>
    <span class="angle3"></span>
    <span class="angle4"></span>
    <div id="char01-1" style="width: 50%;float: left"></div>
    <div id="char01-2" style="width: 50%;float: left"></div>
  </div>
</template>

<script setup>
import * as echarts from "echarts";
import {onMounted, watch} from "vue";

const props = defineProps({
  // 小数点后保留几位
  humidity: {
    type: Number,
    default: 1.0
  },
  temperature: {
    type: Number,
    default: 1.0
  },
})
onMounted(() => {
  const chart1 = echarts.init(document.getElementById('char01-1'), '', {renderer: 'svg'});
  const chart2 = echarts.init(document.getElementById('char01-2'), '', {renderer: 'svg'});

  window.addEventListener('resize', function () {
    chart1.resize();
    chart2.resize();
  });
  chart1.setOption({
    title: {
      text: '湿 度',
      left: 'center',
      bottom: '10px',
      textStyle: {
        color: '#1C5AB3',
        fontSize: 12,
      },
    },
    series: [
      {
        min: 0,
        max: 100,
        type: 'gauge',
        axisLine: {
          lineStyle: {
            width: 15,
            color: [
              [0, '#2CFAFC'],
              [0.33, '#4BAEFD'],
              [0.67, '#FFE24D'],
              [0.99, '#F85C1D'],
              // [1, '#0b275B'] // 底色
            ]
          }
        },
        pointer: {
          width: 3,
        },
        axisTick: {
          distance: -15,
          length: 9,
          lineStyle: {
            color: '#fff',
            width: 1
          }
        },
        splitLine: {
          distance: -15,
          length: 15,
          lineStyle: {
            color: '#ffffff',
            width: 3
          }
        },
        axisLabel: {
          color: 'inherit',
          distance: -15,
          fontSize: 10
        },
        detail: {
          valueAnimation: true,
          fontSize: 15,
          formatter: '{value} %',
          color: 'inherit',
          offsetCenter: [0, '50%']
        },
        data: [
          {
            value: props.temperature
          }
        ]
      }
    ]
  });
  chart2.setOption({
    title: {
      text: '温 度',
      left: 'center',
      bottom: '10px',
      textStyle: {
        color: '#1C5AB3',
        fontSize: 12,
      },
    },
    series: [
      {
        min: 0,
        max: 500,
        type: 'gauge',
        axisLine: {
          lineStyle: {
            width: 15,
            color: [
              [0, '#2CFAFC'],
              [0.33, '#4BAEFD'],
              [0.67, '#FFE24D'],
              [0.99, '#F85C1D'],
              // [1, '#0b275B'] // 底色
            ]
          }
        },
        pointer: {
          width: 3,
        },
        axisTick: {
          distance: -15,
          length: 9,
          lineStyle: {
            color: '#fff',
            width: 1
          }
        },
        splitLine: {
          distance: -15,
          length: 15,
          lineStyle: {
            color: '#ffffff',
            width: 3
          }
        },
        axisLabel: {
          color: 'inherit',
          distance: -15,
          fontSize: 10
        },
        detail: {
          valueAnimation: true,
          fontSize: 15,
          formatter: '{value}°C',
          color: 'inherit',
          offsetCenter: [0, '50%']
        },
        data: [
          {
            value: props.temperature
          }
        ]
      }
    ]
  });
  //监听父组件数据 动态更新数据
  watch(() => props.humidity, (val) => {
    chart1.setOption({
      series: [
        {
          data: [
            {
              value: val
            }
          ]
        }
      ]
    });
  });
});
</script>

<style scoped>

</style>