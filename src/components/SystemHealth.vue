<template>
  <div id="system-health"></div>
</template>
<script>
import echarts from "echarts";
export default {
  name: "SystemHealth",
  mounted() {
    let myChart = echarts.init(document.getElementById("system-health"));

    let data = [
      ["a系统", 76.9, 113760489],
      ["b系统", 78.5, 111389562],
      ["c系统", 80.8, 15503457],
      ["e系统", 81.9, 164395345],
      ["f系统", 76.9, 113768943],
      ["g系统", 78.5, 11389562],
      ["h系统", 80.8, 15503457],
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
        trigger: 'axis',
        axisPointer: {
          type: 'cross'
        }
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
          return Math.sqrt(data[2]) / 5e2;
        },
        label: {
          emphasis: {
            show: true,
            formatter: function (param) {
              return param.data[3];
            },
            position: 'top'
          }
        },
        itemStyle: {
          normal: {
            shadowBlur: 10,
            shadowColor: 'rgba(25, 100, 150, 0.5)',
            shadowOffsetY: 5,
            color: new echarts.graphic.RadialGradient(0.4, 0.3, 1, [{
              offset: 0,
              color: 'rgb(7, 227, 238)'
            }, {
              offset: 1,
              color: 'rgb(25, 183, 207)'
            }])
          }
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

