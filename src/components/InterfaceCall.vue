<template>
  <!-- 接口调用情况 -->
  <div id="interface-call-wrapper">
    <div>
      <div class="title">接口调用情况</div>
      <div class="subtitle">product sell</div>
    </div>
    <div class="column_title_box">
      <div class="column_title">年度(次)</div>
      <div class="column_title">本月(次)</div>
      <div class="column_title">本周(次)</div>
    </div>
    <div class="content_title">接口调用次数排名</div>
    <div class="call_num_box">
      <div class="call_num_column">
        <div class="scroll_container">
          <div class="scroll_content" v-for="(item, index) in yearData">
            <div class="content_index">{{index + 1}}</div>
            <div class="content_info" :title="item">{{item}}</div>
          </div>
        </div>
      </div>
      <div class="call_num_column">
        <div class="scroll_container">
          <div class="scroll_content" v-for="(item, index) in monthData">
            <div class="content_index">{{index + 1}}</div>
            <div class="content_info" :title="item">{{item}}</div>
          </div>
        </div>
      </div>
      <div class="call_num_column">
        <div class="scroll_container">
          <div class="scroll_content" v-for="(item, index) in weekData">
            <div class="content_index">{{index + 1}}</div>
            <div class="content_info" :title="item">{{item}}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="content_title">系统调用排名</div>
    <div class="system_call_box">
      <div class="system_call">1.OA</div>
      <div class="system_call">2.FSCC</div>
      <div class="system_call">3.SAP</div>
    </div>
  </div>
</template>
<script>
export default {
  name: "InterfaceCall",
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
#interface-call-wrapper {
  width: 100%;
  height: 100%;

  .column_title_box {
    display: flex;
    margin: 5px 0;
    font-size: 12px;

    .column_title {
      color: #e8662b;
      flex: 1;
    }
  }

  .call_num_box {
    display: flex;
    font-size: 12px;
    height: calc(100% - 120px);

    .call_num_column {
      flex: 1;
      margin: 2px 5px;
      height: 100%;
      overflow-y: hidden;

      .scroll_container {
        .content_info {
          margin-left: 5px;
          width: calc(100% - 23px);
          height: 20px;
          line-height: 20px;
          text-align: left;
          color: #ddd;
          text-overflow: ellipsis;
          white-space: nowrap;
          overflow: hidden;
        }
      }
    }
  }

  .system_call_box {
    display: flex;

    .system_call {
      flex: 1;
      margin: 0 10px;
      font-size: 12px;
      color: yellow;
      background-color: rgba(4, 49, 98, 0.6);
    }
  }
}
</style>



