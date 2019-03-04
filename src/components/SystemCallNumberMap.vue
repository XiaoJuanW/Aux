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
      title: {
        text: '各系统调用次数',
        left: 'right',
        textStyle: {
          color: '#ddd',
          fontSize: 14
        },
      },
      textStyle: {
        color: "#3b6ade"
      },
      tooltip: {
        trigger: 'axis',
        axisPointer: {
          type: 'cross',
          crossStyle: {
            color: '#999'
          }
        }
      },
      // legend: {
      //   data: ['调用次数', '异常比'],
      //   textStyle: {
      //     color: "#fff"
      //   }
      // },
      xAxis: [
        {
          type: 'category',
          data: ['a系统', 'b系统', 'c系统', 'd系统', 'd系统', 'e系统', 'f系统', 'g系统', 'h系统', 'i系统', 'j系统', 'k系统'],
          axisPointer: {
            type: 'shadow'
          },
          axisLine: {
            lineStyle: {
              color: "#3b6ade"
            }
          },
        }
      ],
      yAxis: [
        {
          type: 'value',
          name: '次数',
          min: 0,
          max: 500,
          interval: 100,
          axisLine: {
            lineStyle: {
              color: "#3b6ade"
            }
          },
          splitLine: {
            show: false  // 不显示水平分割线
          },
        },
        {
          type: 'value',
          name: '异常比',
          min: 0,
          max: 25,
          interval: 5,
          axisLine: {
            lineStyle: {
              color: "#3b6ade"
            }
          },
          splitLine: {
            show: false  // 不显示水平分割线
          },
          axisLabel: {
            formatter: '{value} %'
          }
        }
      ],
      series: [
        {
          name: '调用次数',
          type: 'bar',
          itemStyle: {
            normal: {
              color: function (params) {
                var colorList = [
                  '#084280'
                ];
                return colorList[params.dataIndex]
              }
            }
          },
          data: [220, 490, 400, 232, 256, 367, 135, 162, 326, 200, 64, 33]
        },
        {
          name: '异常比',
          type: 'line',
          yAxisIndex: 1,
          smooth: true,
          itemStyle: {
            normal: {
              color: "#e8662b",
              lineStyle: {
                color: '#e8662b'
              }
            }
          },
          data: [2.0, 2.2, 3.3, 4.5, 6.3, 10.2, 20.3, 23.4, 23.0, 16.5, 12.0, 6.2]
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
#system-call-number {
  width: 100%;
  height: 100%;
}
</style>

