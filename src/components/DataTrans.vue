<template>
  <!-- 数据传输分析 -->
  <div id="data-trans"></div>
</template>
<script>
import echarts from "echarts";
export default {
  name: "DataTrans",
  mounted() {
    let myChart = echarts.init(document.getElementById("data-trans"));
    let option = {
      title: {
        text: '数据传输分析',
        subtext: 'grow for',
        left: 'right',
        textStyle: {
          color: '#ddd',
          fontSize: 14,
        },
        subtextStyle: {
          color: '#998e00'
        }
      },
      tooltip: {
        trigger: 'axis'
      },
      legend: {
        bottom: 0,
        data: [{
          name: "并发流量",
          textStyle: {
            color: '#ddd'
          }
        },
        {
          name: "实时流量",
          textStyle: {
            color: '#ddd'
          }
        }]
      },
      xAxis: {
        type: "category",
        boundaryGap: false,
        data: ["1点", "2点", "3点", "4点", "5点", "6点", "7点"],
        axisLine: {
          lineStyle: {
            color: "#4574da",// 颜色
          }
        }
      },
      yAxis: {
        type: "value",
        axisLine: {
          lineStyle: {
            color: "#4574da" 
          }
        },
        splitLine: {
          show: false  // 不显示水平分割线
        },
      },
      series: [
        {
          name: "并发流量",
          type: "line",
          // lineStyle: {
          //   color: '#ff0000',
          // },
          data: [120, 132, 101, 134, 90, 230, 210]
        },
        {
          name: "实时流量",
          type: "line",
          // lineStyle: {
          //   color: '#008000',
          // },
          data: [220, 182, 191, 234, 290, 330, 310]
        }
      ]
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
#data-trans {
  width: 100%;
  height: 100%;
}
</style>

