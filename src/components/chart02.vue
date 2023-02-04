<template>
  <div class="content">
    <span class="title">条形图</span>
    <span class="angle1"></span>
    <span class="angle2"></span>
    <span class="angle3"></span>
    <span class="angle4"></span>
    <div id="char02"></div>
  </div>
</template>

<script setup>
import * as echarts from "echarts";
import {onMounted} from "vue";

onMounted(() => {
  const chart = echarts.init(document.getElementById('char02'), '', {renderer: 'svg'});
  window.addEventListener('resize', function () {
    chart.resize();
  });
  chart.setOption({
    tooltip: {
      // 虚线
      trigger: 'axis',
      axisPointer: {
        type: 'cross',
      },
      backgroundColor: '#11367a',
      borderWidth: 0,
      padding: 5,
      textStyle: {
        color: '#6dd0e3',
        fontSize: 10,
      },
    },
    legend: {
      data: ['Email', 'Union Ads', 'Video Ads', 'Direct', 'Search Engine'],
      textStyle: {
        color: '#75deef',
        fontSize: 9,
      },
      top: '25px',
      width: '100%',
      left: '0',
      right: '0',

    },
    toolbox: {
      feature: {
        saveAsImage: {} // 保存为图片
      }
    },
    grid: {
      left: '0',
      top: '50px',
      right: '4%',
      bottom: '20px',
      containLabel: true,

    },
    xAxis: [
      {
        type: 'category',
        boundaryGap: false,
        data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
        axisLabel: {
          fontSize: 9,
          color: '#75deef'
        },
      }
    ],
    yAxis: [
      {
        type: 'value',
        axisLabel: {
          fontSize: 9,
          color: '#75deef'
        },
        splitLine: {
          //show: false,// 去掉横线
          lineStyle: {

            color: '#11367a',
          }
        }
      }
    ],
    series: [
      {
        name: 'Email',
        type: 'line',
        stack: 'Total',
        areaStyle: {},
        emphasis: {
          focus: 'series'
        },
        data: [120, 132, 101, 134, 90, 230, 210]
      },
      {
        name: 'Union Ads',
        type: 'line',
        stack: 'Total',
        areaStyle: {},
        emphasis: {
          focus: 'series'
        },
        data: [220, 182, 191, 234, 290, 330, 310]
      },
      {
        name: 'Video Ads',
        type: 'line',
        stack: 'Total',
        areaStyle: {},
        emphasis: {
          focus: 'series'
        },
        data: [150, 232, 201, 154, 190, 330, 410]
      },
      {
        name: 'Direct',
        type: 'line',
        stack: 'Total',
        areaStyle: {},
        emphasis: {
          focus: 'series'
        },
        data: [320, 332, 301, 334, 390, 330, 320]
      },
      {
        name: 'Search Engine',
        type: 'line',
        stack: 'Total',
        label: {
          show: true,
          position: 'top'
        },
        areaStyle: {},
        emphasis: {
          focus: 'series'
        },
        data: [820, 932, 901, 934, 1290, 1330, 1320]
      }
    ]
  });
})
</script>

<style scoped>

</style>