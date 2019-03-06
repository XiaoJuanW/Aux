<template>
  <!-- 排名与统计 -->
  <div id="order-stat-wrapper">
    <div>
      <div class="title">排名与统计</div>
      <div class="subtitle">order stat</div>
    </div>
    <div class="colum_title_box">
      <div class="colum_title_left content_title">接口健康时间排名</div>
      <div class="colum_title_right content_title">系统考评得分</div>
    </div>
    <div class="scroll_box">
      <div class="scroll_container">
        <div class="scroll_content" v-for="(item, index) in list">
          <div class="content_index">{{index + 1}}</div>
          <div class="content_interface_name">{{item.name}}</div>
          <div class="content_sys_name">{{item.sys}}</div>
          <div class="content_percent">
            <span class="content_percent_bg" :style="'width:' + item.percent + '%'"></span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "OrderStat",
  data() {
    return {
      list: [
        { name: '菜单接口', sys: "OA", percent: 90.3 },
        { name: '系统接口', sys: "FSCC", percent: 80 },
        { name: '系统详情接口', sys: "HR", percent: 63 },
        { name: '留言接口', sys: "PLM", percent: 22 },
        { name: '人员同步接口', sys: "HIS", percent: 10 },
        { name: '查看接口', sys: "SAP", percent: 67 },
        { name: '图片接口', sys: "SRM", percent: 55 },
        { name: '个人信息接口', sys: "OMS", percent: 80 }
      ]
    }
  },
  mounted() {
    this.$nextTick(() => {
      // 获取每一条log的高度，计算每一次移动距离
      let logHeight = $(this.$el).find('.scroll_container').children(':first')[0].offsetHeight;
      this.timer = setInterval(() => {
        $(this.$el).find('.scroll_container').animate({
          marginTop: '-' + logHeight + 'px'
        }, 1000, function () {
          $(this).css({ marginTop: "0" }).find(":first").appendTo(this);
        });
      }, 2500);
    });
  },
}
</script>
<style lang="stylus">
#order-stat-wrapper {
  width: 100%;
  height: 100%;

  .colum_title_box {
    display: flex;

    .colum_title_left {
      width: 170px;
    }

    .colum_title_right {
      width: calc(100% - 170px);
    }
  }

  .scroll_box {
    font-size: 12px;
    height: calc(100% - 60px);
    overflow-y: hidden;

    .scroll_container {
      .content_interface_name {
        width: 100px;
        height: 20px;
        line-height: 20px;
        text-align: center;
        color: yellow;
        text-overflow: ellipsis;
        white-space: nowrap;
        overflow: hidden;
      }

      .content_sys_name {
        width: 50px;
        height: 20px;
        line-height: 20px;
        font-size: 12px;
        text-align: left;
      }

      .content_percent {
        position: relative;
        width: calc(100% - 200px);
        height: 10px;
        margin: auto 0;
        border: 1px solid rgb(70, 105, 150);
        border-radius: 10px;

        .content_percent_bg {
          position: absolute;
          top: 0;
          bottom: 0;
          left: 0;
          background: url('../img/progress_bg.jpg');
          background-position: 2px 2px; // 背景图起始点
          background-size: calc(100% - 4px) calc(100% - 4px); // 背景图大小
          background-repeat: no-repeat;
        }
      }
    }
  }
}
</style>



