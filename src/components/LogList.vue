<template>
  <!-- 日志 -->
  <div class="log_wrapper">
    <div class="log_container">
      <div class="log_content" v-for="(item, index) in list">
        <div class="index_content">{{index + 1}}</div>
        <div class="text">{{item}}</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "LogList",
  data() {
    return {
      timer: null, // 定时器
      list: [
        "日志信息1日志信息1日志信息1日志信息1日志信息1日志信息1日志信息1日志信息1日志信息1",
        "日志信息2日志信息2日志信息2",
        "日志信息3日志信息3日志信息3",
        "日志信息4日志信息4日志信息4",
        "日志信息5日志信息5日志信息5",
        "日志信息2日志信息2日志信息2",
        "日志信息3日志信息3日志信息3",
        "日志信息4日志信息4日志信息4",
        "日志信息5日志信息5日志信息5",
        "日志信息2日志信息2日志信息2",
        "日志信息3日志信息3日志信息3",
        "日志信息4日志信息4日志信息4",
        "日志信息5日志信息5日志信息5"
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
.log_wrapper {
  width: 100%;
  height: 100%;
  overflow-y: hidden;

  .log_content {
    position: relative;
    display: flex;
    padding-bottom: 5px;

    .index_content {
      width: 22px;
      height: 22px;
      line-height: 22px;
      border-radius: 11px;
      background-color: rgb(110, 208, 205);
      font-size: 10px;
    }

    .text {
      margin-left: 5px;
      width: calc(100% - 30px);
      height: 22px;
      line-height: 22px;
      text-align: left;
      background-color: rgba(20, 59, 102, 0.5);
      color: rgb(169, 125, 49);
      font-size: 10px;
      text-overflow: ellipsis;
      white-space: nowrap;
      overflow: hidden;
    }
  }
}
</style>


