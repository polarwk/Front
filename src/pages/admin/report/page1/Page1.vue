<template>
  <div ref="simpleBarChart" style="width: 600px; height: 400px;"></div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import * as echarts from 'echarts';
import myStore from "../../../../stores/myStore";

const infoTiles = ref([
  {
    color: 'info',
    value: EM_fossil,
    text: 'sum(EM_fossil)',
    icon: '',
  },
  {
    color: 'info',
    value: EM_elec,
    text: 'sum(EM_elec)',
    icon: '',
  },
  {
    color: 'info',
    value: EM_chemi,
    text: 'sum(EM_chemi)',
    icon: '',
  },
  {
    color: 'success',
    value: EM_process,
    text: 'EM_process',
    icon: '',
  },
  {
    color: 'success',
    value: myStore.state.EM_transport,
    text: 'EM_transport',
    icon: '',
  },
  {
    color: 'success',
    value: EM_recyc,
    text: 'EM_recyc',
    icon: '',
  },
])

const simpleBarChart = ref(null);

onMounted(() => {
  const chart = echarts.init(simpleBarChart.value);

  const option = {
    title: {
      text: '排放量对比'
    },
    xAxis: {
      type: 'category',
      data: ['基准线情景排放量', '资源化情景排放量']
    },
    yAxis: {
      type: 'value'
    },
    series: [
      {
        data: [
          { value: 61673.64, itemStyle: { color: '#5470C6' } },
          { value: 17195.35, itemStyle: { color: '#91CC75' } }
        ],
        type: 'bar',
        label: {
          show: true,
          position: 'top',
          formatter: function(params) {
            return params.value.toLocaleString(); // 使用toLocaleString()方法添加千位分隔符
          }
        }
      }
    ]
  };

  chart.setOption(option);
});
</script>
