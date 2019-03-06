<template>
  <div class="main_container">
    <div class="nav_container">
      <navi-bar></navi-bar>
    </div>
    <div class="main_content">
      <div class="main_content_left">
        <div class="block_bg pruduct_sell">
          <interface-call></interface-call>
        </div>
        <div class="block_bg normal_log">
          <log-list :error="false" :title="normalTitle" :subtitle="normalSubtitle"></log-list>
        </div>
        <div class="systematic_health">
          <system-health></system-health>
        </div>
      </div>
      <div class="main_content_center">
        <div class="system_distribution_map">
          <system-distribution-map></system-distribution-map>
        </div>
        <div class="system_call_number">
          <system-call-number-map></system-call-number-map>
        </div>
      </div>
      <div class="main_content_right">
        <div class="block_bg grow_for">
          <data-trans></data-trans>
        </div>
        <div class="block_bg order_stat">
          <order-stat></order-stat>
        </div>
        <div class="block_bg error_log">
          <log-list :error="true" :title="errorTitle" :subtitle="errorSubtitle"></log-list>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NaviBar from "@/components/NaviBar.vue";
import InterfaceCall from "@/components/InterfaceCall.vue";
import LogList from "@/components/LogList.vue";
import SystemHealth from "@/components/SystemHealth.vue";
import SystemDistributionMap from "@/components/SystemDistributionMap.vue";
import SystemCallNumberMap from "@/components/SystemCallNumberMap.vue";
import DataTrans from "@/components/DataTrans.vue";
import OrderStat from "@/components/OrderAndStat.vue";

export default {
  name: "Mainview",
  components: {
    NaviBar,
    InterfaceCall,
    SystemDistributionMap,
    SystemCallNumberMap,
    SystemHealth,
    LogList,
    DataTrans,
    OrderStat
  },
  methods: {},
  created() { },
  data() {
    return {
      normalTitle: '正常日志',
      normalSubtitle: 'normal log',
      errorTitle: '错误日志',
      errorSubtitle: 'error log',
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus">
.main_container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: url('../img/bg.jpg');
  background-size: 100% 100%;
  box-sizing: border-box;
  padding: 60px 20px 0 20px;
  display: flex;
  color: white;

  .nav_container {
    position: absolute;
    left: 20px;
    right: 20px;
    top: 0;
    height: 60px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.3);
  }

  .main_content {
    display: flex;
    width: 100%;
    height: 100%;

    .main_content_left {
      width: 30%;
      height: 100%;

      .pruduct_sell {
        height: 40%;
      }

      .normal_log {
        height: 30%;
      }

      .systematic_health {
        width: 100%;
        height: 30%;
      }
    }

    .main_content_center {
      width: 40%;
      height: 100%;

      .system_distribution_map {
        width: 100%;
        height: 70%;
      }

      .system_call_number {
        width: 100%;
        height: 30%;
      }
    }

    .main_content_right {
      width: 30%;
      height: 100%;

      .grow_for {
        height: 40%;
      }

      .order_stat {
        height: 30%;
      }

      .error_log {
        height: 30%;
      }
    }
  }
}

.block_bg {
  width: 100%;
  background-image: url('../img/formBg.png');
  background-size: 100% calc(100% - 20px);
  background-position: 0 10px;
  background-repeat: no-repeat;
  padding: 20px 15px;
  box-sizing: border-box;
}
</style>
