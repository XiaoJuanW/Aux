<template>
  <!-- 日志 -->
  <div id="log-wrapper">
    <div>
      <div class="title">{{title}}</div>
      <div class="subtitle">{{subtitle}}</div>
    </div>
    <div class="log_box">
      <div class="log_container">
        <div class="log_content" v-for="(item, index) in list">
          <div class="log_index">{{index + 1}}</div>
          <div class="log_wrap">
            <span class="log_time">{{item.time}}</span>
            <div :class="error ? 'error log_info' : 'log_info'">{{item.log}}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "LogList",
  props: {
    title: {
      type: String,
    },
    subtitle: {
      type: String,
    },
    error: {
      type: Boolean,
    }
  },
  data() {
    return {
      timer: null, // 定时器
      list: [
        { time: '10.01', log: "日志信息1日志信息1日志信息1日志}信息1日志信息1日志信息1日志信息1日志信息1日志信息1" },
        { time: '10.02', log: "日志信息2日志信息2日志信息2日志信息2日志信息2日志信息2日志信息2日志信息2日志信息2" },
        { time: '10.03', log: "日志信息3日志信息3日志信息3日志信息3日志信息3日志信息3日志信息3日志信息3日志信息3" },
        { time: '11.04', log: "日志信息4日志信息4日志信息4日志信息3日志信息3日志信息3日志信息3日志信息3日志信息3" },
        { time: '11.05', log: "日志信息5日志信息5日志信息5日志信息3日志信息3日志信息3" },
        { time: '15.06', log: "日志信息2日志信息2日志信息2日志信息3日志信息3日志信息3" },
        { time: '15.07', log: "日志信息3日志信息3日志信息3日志信息3日志信息3日志信息3" },
        { time: '15.08', log: "日志信息4日志信息4日志信息4日志信息3日志信息3日志信息3" },
        { time: '16.09', log: "日志信息5日志信息5日志信息5日志信息3日志信息3日志信息3" },
        { time: '17.10', log: "日志信息2日志信息2日志信息2日志信息3日志信息3日志信息3" },
        { time: '18.11', log: "日志信息3日志信息3日志信息3日志信息3日志信息3日志信息3" },
        { time: '19.12', log: "日志信息4日志信息4日志信息4日志信息3日志信息3日志信息3" },
        { time: '19.13', log: "日志信息5日志信息5日志信息5日志信息3日志信息3日志信息3" }
      ]
    };
  },
  mounted() {
    this.$nextTick(() => {
      // 获取每一条log的高度，计算每一次移动距离
      let logHeight = $(this.$el).find('.log_container').children(':first')[0].offsetHeight;
      this.timer = setInterval(() => {
        $(this.$el).find('.log_container').animate({
          marginTop: '-' + logHeight + 'px'
        }, 1000, function () {
          $(this).css({ marginTop: "0" }).find(":first").appendTo(this);
        });
      }, 2500);
    });
  },
  beforeDestroy() {
    // 销毁定时器
    clearInterval(this.timer);
    this.timer = null;
  }
};
</script>
<style scope lang="stylus">
#log-wrapper {
  width: 100%;
  height: 100%;

  .log_box {
    width: 100%;
    height: calc(100% - 32px);
    overflow-y: hidden;

    .log_container {
      .log_content {
        display: flex;
        padding-bottom: 3px;

        .log_index {
          width: 24px;
          height: 24px;
          line-height: 24px;
          border-radius: 5px;
          background-color: #4de2e2;
          font-size: 10px;
          margin: auto;
        }

        .log_wrap {
          margin-left: 5px;
          width: calc(100% - 30px);
          text-align: left;

          .log_time {
            font-size: 10px;
            color: #ddd;
            text-align: left;
          }

          .log_info {
            width: calc(100% - 30px);
            color: green;
            font-size: 12px;
            text-overflow: ellipsis;
            white-space: nowrap;
            overflow: hidden;
          }

          .error {
            color: yellow;
          }
        }
      }
    }
  }
}
</style>


