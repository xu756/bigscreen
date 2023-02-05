<template>
  <div class="content">
    <span class="title">条形图</span>
    <span class="angle1"></span>
    <span class="angle2"></span>
    <span class="angle3"></span>
    <span class="angle4"></span>
    <div id="char01"></div>
  </div>
</template>

<script setup>
import * as echarts from "echarts";
import {onMounted} from "vue";

onMounted(() => {
  const chart = echarts.init(document.getElementById('char01'), '', {renderer: 'svg'});
  window.addEventListener('resize', function () {
    chart.resize();
  });
  chart.setOption({
    xAxis: {
      data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
      axisLabel: {
        interval: 0,
        fontSize: 9,
        color: '#75deef'
      },
    },
    grid: {
      top: "30px",
      left: '3%',
      right: '3%',
      bottom: '3%',
      containLabel: true,
    },
    yAxis: {
      max: 30,
    },
    series: [
      {
        type: 'bar',
        data: [23, 24, 18, 25, 27, 28, 25]
      },
      {
        type: 'bar',
        data: [26, 24, 18, 22, 23, 20, 27]
      },
    ], tooltip: {
      trigger: 'axis',
      axisPointer: {
        type: 'shadow'
      }
    },
  });
})
</script>

<style scoped>

</style>