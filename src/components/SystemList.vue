<template>
<!-- 系统列表 -->
  <div>
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
          <tr
            v-for="(item, index) in list"
            v-if="index < 3"
          >
            <td>{{item.code}}</td>
            <td>{{item.name}}</td>
            <td>{{item.event}}</td>
            <td>{{item.charge}}</td>
            <td>{{item.time}}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
  <!-- <div class="index_content"></div>
      <div class="text"></div>
      <div class="text"></div>
      <div class="text"></div>
      <div class="text"></div> -->

  <!-- <div
      class="list_container"
      v-for="(item, index) in list"
    >
      <div class="">{{item.code}}</div>
      <div class="text">{{item.name}}</div>
      <div class="text">{{item.event}}</div>
      <div class="text">{{item.charge}}</div>
      <div class="text">{{item.time}}</div>
    </div> -->
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
        },
        {
          code: "002",
          name: "OA",
          event: "系统统载",
          charge: "李四",
          time: "20190122"
        },
        {
          code: "003",
          name: "OA",
          event: "系统统载",
          charge: "王二",
          time: "20190122"
        },
        {
          code: "004",
          name: "OA",
          event: "系统统载",
          charge: "张三",
          time: "20190122"
        },
        {
          code: "005",
          name: "OA",
          event: "系统统载",
          charge: "张三",
          time: "20190122"
        },
        {
          code: "006",
          name: "OA",
          event: "系统统载",
          charge: "张三",
          time: "20190122"
        }
      ]
    };
  }
};
</script>
<style lang="stylus">
.table_container {
}

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
  text-align left ;
}

</style>


