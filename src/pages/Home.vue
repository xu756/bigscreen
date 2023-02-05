<template>
  <div class="box-a">
    <div class="charts">
      <Chart01 :humidity="equipment.humidity" :temperature="equipment.temperature"></Chart01>
    </div>
    <div class="charts"></div>
    <div class="charts"></div>
  </div>
  <div class="box-b"></div>
  <div class="box-c"></div>
</template>

<script setup>
import Chart01 from "../components/chart01.vue";
import {onMounted, ref} from "vue";

let equipment = ref({
  humidity: 1.0,
  temperature: 1.0,
})
onMounted(() => {
      setInterval(() => {
        equipment.value.humidity = equipment.value.humidity + 1;
      }, 1000);
    },
);

</script>

<style scoped>

</style>