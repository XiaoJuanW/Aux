<template>
  <!-- 系统健康度 -->
  <div id="system-health"></div>
</template>
<script>
import echarts from "echarts";
export default {
  name: "SystemHealth",
  mounted() {
    let myChart = echarts.init(document.getElementById("system-health"));

    let data = [
      ["a系统", 90.9],
      ["b系统", 78.5],
      ["c系统", 60.8],
      ["e系统", 31.9],
      ["f系统", 50.9],
      ["g系统", 38.5],
      ["h系统", 100],
    ];

    let option = {
      title: {
        text: '系统健康度',
        subtext: 'systematic health',
        left: 'right',
        textStyle: {
          color: '#ddd',
          fontSize: 14
        },
        subtextStyle: {
          color: '#998e00'
        }
      },
      tooltip: {
        trigger: 'axis'
      },
      xAxis: {
        axisLine: {
          lineStyle: {
            color: "#ddd"
          }
        },
        data: ['a系统', 'b系统', 'c系统', 'd系统', 'e系统', 'f系统', 'g系统', 'h系统']
      },
      yAxis: {
        type: 'value',
        axisLine: {
          lineStyle: {
            color: "#ddd"
          }
        },
        splitLine: {
          show: false  // 不显示水平分割线
        },
      },
      series: [{
        name: '健康度',
        type: 'scatter',
        symbolSize: function (data) {
          let size = Math.sqrt(data[1]) * 2;
          return size;
        },
        label: {
          emphasis: {
            show: true,
          }
        },
        itemStyle: {
          color: function (data) {
            if (data.value[1] > 60) {
              return '#57bf57';
            } else {
              return '#ca4646';
            }
          },
        },
        data: data
      }]
    };
    myChart.setOption(option);

    //建议加上以下这一行代码，不加的效果图如下（当浏览器窗口缩小的时候）。超过了div的界限（红色边框）
    window.addEventListener("resize", function () {
      myChart.resize();
    });
  },
  methods: {},
  watch: {},
  created() { }
};
</script>
<style lang="stylus">
#system-health {
  width: 100%;
  height: 100%;
}
</style>

