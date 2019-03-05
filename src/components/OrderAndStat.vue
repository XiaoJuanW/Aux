<template>
  <div class="order_stat_wrapper">
    <div class="title_box">
      <div class="title">排名与统计</div>
      <div class="subtitle">order stat</div>
    </div>
    <div class="colum_title_box">
      <div class="colum_title_left">接口健康时间排名</div>
      <div class="colum_title_right">系统考评得分</div>
    </div>
    <div class="call_num_box">
      <div class="call_num_colum">
        <div class="call_num_container">
          <div class="call_num_content" v-for="(item, index) in list">
            <div class="index_call_num">{{index + 1}}</div>
            <div class="call_num_text">{{item.name}}</div>
            <div class="call_num_sys">{{item.sys}}</div>
            <div class="call_num_percent">
              <span class="call_num_percent_bg" :style="'width:' + item.percent + '%'"></span>
            </div>
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
      let logHeight = $(this.$el).find('.call_num_container').children(':first')[0].offsetHeight;
      this.timer = setInterval(() => {
        $(this.$el).find('.call_num_container').animate({
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
.order_stat_wrapper {
  width: 100%;
  height: 100%;

  .title_box {
    .title {
      font-size: 14px;
      color: #ddd;
      text-align: right;
    }

    .subtitle {
      font-size: 12px;
      color: #998e00;
      text-align: right;
    }
  }

  .colum_title_box {
    display: flex;
    margin-top: 5px;
    font-size: 12px;
    color: 12px;

    .colum_title_left {
      width: 30%;
    }

    .colum_title_right {
      width: 70%;
    }
  }

  .call_num_box {
    display: flex;
    font-size: 12px;
    height: calc(100% - 50px);

    .call_num_colum {
      margin: 2px 5px;
      width: 100%;
      height: 100%;
      overflow-y: hidden;

      .call_num_container {
        overflow-y: hidden;

        .call_num_content {
          display: flex;
          height: 20px;
          padding-bottom: 5px;

          .index_call_num {
            width: 18px;
            height: 18px;
            line-height: 18px;
            margin: auto 0;
            border-radius: 9px;
            background-color: cyan;
          }

          .call_num_text {
            width: 80px;
            height: 20px;
            line-height: 20px;
            text-align: center;
            color: yellow;
            text-overflow: ellipsis;
            white-space: nowrap;
            overflow: hidden;
          }

          .call_num_sys {
            width: 40px;
            height: 20px;
            line-height: 20px;
            font-size: 12px;
            text-align: left;
          }

          .call_num_percent {
            position: relative;
            width: calc(100% - 145px);
            height: 10px;
            margin: auto 0;
            border: 1px solid rgb(70, 105, 150);
            border-radius: 10px;

            .call_num_percent_bg {
              position: absolute;
              top: 0;
              bottom: 0;
              left: 0;
              width: 90px;
              background: url('../img/progress_bg.jpg');
              background-position: 2px 2px;
              background-size: calc(100% - 4px) calc(100% - 4px);
              background-repeat: no-repeat;
            }
          }
        }
      }
    }
  }
}
</style>



