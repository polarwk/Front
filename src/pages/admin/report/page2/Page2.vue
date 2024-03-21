<template>
  <div ref="barChart" style="width: 600px; height: 400px;"></div>


</template>

<script>
import { ref, onMounted } from 'vue';
import * as echarts from 'echarts';

export default {
  name: 'BarChart',
  setup() {
    const barChart = ref(null);

    onMounted(() => {
      const chart = echarts.init(barChart.value);

      const option = {
        title: {
          text: '该汇报年度的碳减排绩效',
          left: 'left'
        },
        legend: {
          data: ['基准线情景', '资源化情景'],
          top: 30
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '3%',
          containLabel: true
        },
        xAxis: {
          type: 'category',
          data: ['原料替代', '焚烧+填埋', '运输', '化石燃料', '电力消耗', '辅料添加']
        },
        yAxis: {
          type: 'value'
        },
        series: [
          {
            name: '基准线情景',
            type: 'bar',
            stack: '总量',
            label: {
              show: true,
              position: 'top',
              formatter: (params) => {
                if (params.value !== '-') {
                  return params.value.toLocaleString(); // 使用toLocaleString()方法添加千位分隔符
                } else {
                  return '-';
                }
              },
              emphasis: {
                show: true
              }
            },
            itemStyle: {
              color: '#5470c6' // 基准线情景的颜色
            },
            data: [33154, 10228, 76, '-', '-', '-'] // 使用'-'代替数值为0的数据
          },
          {
            name: '资源化情景',
            type: 'bar',
            stack: '总量',
            label: {
              show: true,
              position: 'top',
              formatter: (params) => {
                if (params.value !== '-') {
                  return params.value.toLocaleString(); // 使用toLocaleString()方法添加千位分隔符
                } else {
                  return '-';
                }
              },
              emphasis: {
                show: true
              }
            },
            itemStyle: {
              color: '#91cc75' // 资源化情景的颜色
            },
            data: ['-', '-', '-', 8562, 12428, 190] // 使用'-'代替数值为0的数据
          }
        ]
      };

      chart.setOption(option);
    });

    return {
      barChart
    };
  }
};
</script>

<style scoped>
/* 可以根据需要添加样式 */
</style>
