<template>
  <div id="system-call-number"></div>
</template>
<script>
import echarts from "echarts";
export default {
  name: "SystemCallNumberMap",
  mounted() {
    let myChart = echarts.init(document.getElementById("system-call-number"));
    let option = {
      textStyle: {
        color: "#fff"
      },
      title: {
        text: "各系统调用次数",
        textStyle: {
          color: "#fff"
        }
      },
      tooltip: {
        trigger: "axis"
      },
      // legend: {
      //   data: ["服务调用总数", "传输成功总数", "传输失败总数"],
      //   textStyle: {
      //     color: "#fff"
      //   }
      // },
      grid: {
        left: "3%",
        right: "4%",
        bottom: "3%",
        containLabel: true
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
            color: "#fff" // 颜色
            //width: 2 // 粗细
          }
        }
      },
      yAxis: {
        type: "value",
        axisLine: {
          lineStyle: {
            color: "#fff" // 颜色
            //width: 2 // 粗细
          }
        }
      },
      series: [
        {
          name: "服务调用总数",
          type: "line",
          stack: "总量",
          smooth: true,  // 曲线
          data: [120, 132, 101, 134, 90, 230, 210]
        },
        {
          name: "传输成功总数",
          type: "line",
          stack: "总量",
          data: [220, 182, 191, 234, 290, 330, 310]
        },
        {
          name: "传输失败总数",
          type: "line",
          stack: "总量",
          data: [150, 232, 201, 154, 190, 330, 410]
        }
      ]
    };

    myChart.setOption(option);

    //建议加上以下这一行代码，不加的效果图如下（当浏览器窗口缩小的时候）。超过了div的界限（红色边框）
    window.addEventListener("resize", function() {
      myChart.resize();
    });
  },
  methods: {},
  watch: {},
  created() {}
};
</script>
<style lang="stylus">
#system-call-number {
  width: 100%;
  height: 100%;
}
</style>

