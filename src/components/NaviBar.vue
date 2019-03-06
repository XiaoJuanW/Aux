<template>
  <div id="nav-wrapper">
    <div class="nav_left">
      <span class="nav_left_letter">AUX 奥克斯</span>
    </div>
    <div class="nav_center">
      <div class="nav_center_title">AUX系统地图</div>
      <span class="nav_center_date">2019年2月23日 星期三</span>
      <span class="nav_center_time">04:04:34</span>
    </div>
    <div class="nav_right">
      <div class="nav_right_days">已监控多少天：98天</div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'NaviBar'
}
</script>
<style lang="stylus">
#nav-wrapper {
  height: 100%;
  width: 100%;
  display: flex;

  .nav_left {
    width: 25%;
    text-align: left;

    .nav_left_letter {
      line-height: 60px;
      font-size: 30px;
      font-weight: 800;
    }
  }

  .nav_center {
    width: 50%;

    .nav_center_title {
      margin: 9px auto;
      font-size: 25px;
    }

    .nav_center_date {
      color: rgb(232, 102, 43);
      font-size: 12px;
    }

    .nav_center_time {
      color: #ddd;
      font-size: 12px;
    }
  }

  .nav_right {
    position: relative;
    width: 25%;
    text-align: right;

    .nav_right_days {
      position: absolute;
      bottom: 3px;
      right: 0;
      font-size: 12px;
      color: rgb(232, 102, 43);
    }
  }
}
</style>
