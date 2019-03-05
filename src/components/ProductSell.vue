<template>
  <div class="product_sell_wrapper">
    <div class="title_box">
      <div class="title">接口调用情况</div>
      <div class="subtitle">product sell</div>
    </div>
    <div class="colum_title_box">
      <div class="colum_title">年度</div>
      <div class="colum_title">本月</div>
      <div class="colum_title">本周</div>
    </div>
    <div class="call_num_order">接口调用次数排名</div>
    <div class="call_num_box">
      <div class="call_num_colum">
        <div class="call_num_container">
          <div class="call_num_content" v-for="(item, index) in yearData">
            <div class="index_call_num">{{index + 1}}</div>
            <div class="call_num_text" :title="item">{{item}}</div>
          </div>
        </div>
      </div>
      <div class="call_num_colum">
        <div class="call_num_container">
          <div class="call_num_content" v-for="(item, index) in monthData">
            <div class="index_call_num">{{index + 1}}</div>
            <div class="call_num_text" :title="item">{{item}}</div>
          </div>
        </div>
      </div>
      <div class="call_num_colum">
        <div class="call_num_container">
          <div class="call_num_content" v-for="(item, index) in weekData">
            <div class="index_call_num">{{index + 1}}</div>
            <div class="call_num_text" :title="item">{{item}}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="call_num_order">系统调用排名</div>
    <div class="system_call_box">
      <div class="system_call">1.OA</div>
      <div class="system_call">2.FSCC</div>
      <div class="system_call">3.SAP</div>
    </div>
  </div>
</template>
<script>
export default {
  name: "ProductSell",
  data() {
    return {
      yearData: ['A接口调用1000次', 'B接口调用900次', 'C接口调用800次', 'D接口调用700次', 'E接口调用600次', 'F接口调用500次', 'F接口调用500次', 'F接口调用500次'],
      monthData: ['A接口调用100次', 'B接口调用90次', 'C接口调用80次', 'D接口调用70次', 'E接口调用60次', 'F接口调用50次'],
      weekData: ['A接口调用10次', 'B接口调用9次', 'C接口调用8次', 'D接口调用7次', 'E接口调用6次', 'F接口调用5次'],
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
.product_sell_wrapper {
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

    .colum_title {
      color: #e8662b;
      flex: 1;
    }
  }

  .call_num_order {
    margin-top: 5px;
    text-align: left;
    font-size: 12px;
  }

  .call_num_box {
    display: flex;
    font-size: 12px;
    height: calc(100% - 100px);

    .call_num_colum {
      flex: 1;
      margin: 2px 5px;
      height: 100%;
      overflow-y: hidden;

      .call_num_container {
        overflow-y: hidden;

        .call_num_content {
          display: flex;
          height: 20px;
          // margin-bottom 5px;
          // background-color: rgba(4, 49, 98, 0.6);

          .index_call_num {
            width: 18px;
            height: 18px;
            line-height: 18px;
            margin: auto;
            border-radius: 9px;
            background-color: cyan;
          }

          .call_num_text {
            width: calc(100% - 23px);
            height: 20px;
            line-height: 20px;
            text-align: left;
            text-overflow: ellipsis;
            white-space: nowrap;
            overflow: hidden;
          }
        }
      }
    }
  }

  .system_call_box {
    display: flex;

    .system_call {
      flex: 1;
      margin: 10px;
      font-size: 12px;
      color: yellow;
      background-color: rgba(4, 49, 98, 0.6);
    }
  }
}
</style>



