<template>
  <!-- 系统列表 -->
  <div class="table_container">
    <table>
      <thead>
        <tr>
          <th>系统编码</th>
          <th>系统名称</th>
          <th>事件</th>
          <th>系统负责人</th>
          <th>警告时间</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in list">
          <td>{{item.code}}</td>
          <td>{{item.name}}</td>
          <td>{{item.event}}</td>
          <td>{{item.charge}}</td>
          <td>{{item.time}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
export default {
  name: "SystemList",
  data() {
    return {
      list: [
        {
          code: "001",
          name: "OA",
          event: "系统统载",
          charge: "张三",
          time: "20190122"
        }, {
          code: "002",
          name: "MS",
          event: "系统统载",
          charge: "李四",
          time: "20190123"
        }, {
          code: "003",
          name: "AB",
          event: "系统统载",
          charge: "王二",
          time: "20190124"
        }, {
          code: "004",
          name: "OPS",
          event: "系统统载",
          charge: "张三",
          time: "20190125"
        }, {
          code: "005",
          name: "LAS",
          event: "系统统载",
          charge: "张三",
          time: "20190126"
        }, {
          code: "006",
          name: "MMS",
          event: "系统统载",
          charge: "张三",
          time: "20190127"
        }
      ]
    };
  },
  mounted() {
    this.$nextTick(() => {
      let height = $(this.$el).find('tbody').children(':first')[0].offsetHeight;
      this.timer = setInterval(() => {
        $(this.$el).find('tbody').animate({
          marginTop: '-' + height + 'px'
        }, 1000, function () {
          $(this).css({ marginTop: "0" }).find(":first").appendTo(this);
        });
      }, 2500);
    });
  }
};
</script>
<style lang="stylus">
table {
  margin: 20px auto;
  width: 90%;
}

th, td {
  // border: 1px solid rgba(255, 255, 255, 0.6);
  height: 30px;
  line-height: 30px;
  font-size: 15px;
  color: rgb(140, 230, 74);
  text-align: left;
}
</style>


