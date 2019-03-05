<template>
  <div id="echart"></div>
</template>
<script>
import echarts from "echarts";
export default {
  name: "DisplayMap",
  mounted() {
    let myChart = echarts.init(document.getElementById("echart"));
    let option = {
      title: {
        text: '数据传输分析',
        subtext: 'grow for',
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
        trigger: "axis"
      },
      legend: {
        bottom: 0,
        data: ["并发流量", "实时流量"],
        textStyle: {
          color: "#fff"
        }
      },
      toolbox: {
        feature: {
          // saveAsImage: {}
        }
      },
      xAxis: {
        type: "category",
        boundaryGap: false,
        data: ["1点", "2点", "3点", "4点", "5点", "6点", "7点"],
        axisLine: {
          lineStyle: {
            color: "#3b6ade" // 颜色
            //width: 2 // 粗细
          }
        },
        // splitLine: {
        //   lineStyle: {
        //     // 使用深浅的间隔色
        //     color: ['#aaa', '#ddd']
        //   }
        // }
      },
      yAxis: {
        type: "value",
        axisLine: {
          lineStyle: {
            color: "#3b6ade" // 颜色
            //width: 2 // 粗细
          }
        },
        splitLine: {
          show: false  // 不显示水平分割线
        },
      },
      series: [
        {
          name: "服务调用总数",
          type: "line",
          stack: "总量",
          data: [120, 132, 101, 134, 90, 230, 210]
        },
        {
          name: "传输成功总数",
          type: "line",
          stack: "总量",
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
#echart {
  width: 100%;
  height: 100%;
}
</style>

