<template>
  <!-- 系统分块图 -->
  <div class="distribution_map_container">
    <div class="distribution_map_content">
      <div class="top_wrapper">
        <div v-for="(item, index) in top" :class="(item.status == -1) ? 'service_block error': 'service_block'">
          <div class="title">{{item.sys}}</div>
          <div class="name">{{item.name}}</div>
          <div :class="(item.status == 1) ? 'normal_light' : (item.status == -1 ? 'abnormal_light' : 'sys_light')">
          </div>
        </div>
      </div>
      <div class="esb_container">
        <div class="esb" id="esb">ESB</div>
      </div>
      <div class="bottom_wrapper">
        <div v-for="(item, index) in bottom" :class="(item.status == -1) ? 'service_block error': 'service_block'">
          <div class="title">{{item.sys}}</div>
          <div class="name">{{item.name}}</div>
          <div :class="(item.status == 1) ? 'normal_light' : (item.status == -1 ? 'abnormal_light' : 'sys_light')">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "SystemDistributionMap",
  mounted() {
    let x, y, toX, toY, lineColor;
    let html = "";
    $('.top_wrapper').children().each(function (index, ele) {
      lineColor = ele.className.indexOf('error') > -1 ? '#ff000099' : '#ffffff4d';
      x = ele.offsetLeft + ele.clientWidth / 2, y = ele.offsetTop + ele.clientHeight;
      $('.esb_container').children().each(function (index, ele) {
        toX = ele.offsetLeft + ele.clientWidth / 2, toY = ele.offsetTop;
      });
      html += '<div class="svg_block" >';
      html += '<svg class="svg_line" width="100%" height="100%" version="1.1" xmlns="http://www.w3.org/2000/svg">';
      html += '<path class="path" stroke="' + lineColor + '" stroke-width="1" d="M ' + x + ' ' + y + ' ' + x + ' ' + toY + '" />';
      html += "</svg>";
      html += "</div>";
    });
    // let html = linkLine('.top_wrapper', '.esb_container', true);
    $(".distribution_map_content").append(html);

    let x2, y2, toX2, toY2, lineColor2;
    let html2 = "";
    $('.bottom_wrapper').children().each(function (index, ele) {
      x2 = ele.offsetLeft + ele.clientWidth / 2, y2 = ele.offsetTop;
      lineColor2 = ele.className.indexOf('error') > -1 ? '#ff000099' : '#ffffff4d';

      $('.esb_container').children().each(function (index, ele) {
        toX2 = ele.offsetLeft + ele.clientWidth / 2, toY2 = ele.offsetTop + ele.clientHeight;
      });
      html2 += '<div class="svg_block">';
      html2 += '<svg class="svg_line" width="100%" height="100%" version="1.1" xmlns="http://www.w3.org/2000/svg">';
      html2 += '<path class="path" stroke="' + lineColor2 + '" stroke-width="1" d="M ' + x2 + ' ' + y2 + ' ' + x2 + ' ' + toY2 + '" />';
      html2 += "</svg>";
      html2 += "</div>";
    });
    $(".distribution_map_content").append(html2);
  },
  created() {

  },
  methods: {
    linkLine(fromEle, toEle, isTop) {
      let x, y, toX, toY;
      let html = "";
      $(fromEle).children().each(function (index, ele) {
        x = ele.offsetLeft + ele.clientWidth / 2, y = ele.offsetTop + (isTop ? ele.clientHeight : 0);
        $(toEle).children().each(function (index, ele) {
          toX = ele.offsetLeft + ele.clientWidth / 2, toY = ele.offsetTop + ele.clientHeight / 2;
        });
        html += '<div class="svg_block">';
        html += '<svg class="svg_line" width="100%" height="100%" version="1.1" xmlns="http://www.w3.org/2000/svg">';
        html += '<path class="path" stroke="#ffffff4d" stroke-width="1" d="M ' + x + ' ' + y + ' ' + toX + ' ' + toY + '" />';
        html += "</svg>";
        html += "</div>";
      });
      return html;
    }
  },
  data() {
    return {
      top: [{ sys: '集团', name: 'OA', status: 1 },  // status 1正常  -1异常  0系统 
      { sys: '集团', name: 'MDM', status: -1 },
      { sys: '集团', name: 'FSSC', status: 0 },
      { sys: '集团', name: 'HR', status: -1 },
      { sys: '电力', name: 'FIS', status: 1 },
      { sys: '电力', name: 'PLM', status: 1 }],
      bottom: [{ sys: '家电', name: 'PDM', status: -1 },
      { sys: '家电', name: 'OMS', status: 1 },
      { sys: '家电', name: 'IMS', status: 1 },
      { sys: '家电', name: 'SRM', status: 0 },
      { sys: '家电', name: 'SAP', status: -1 },
      { sys: '医疗', name: 'HIS', status: -1 }]
    };
  }
};
</script>
<style lang="stylus">
.distribution_map_container {
  position: relative;
  padding: 15px;
  height: 100%;
  box-sizing: border-box;

  .distribution_map_content {
    width: 100%;
    height: 100%;

    .top_wrapper, .bottom_wrapper {
      display: flex;
      height: 20%;

      .service_block {
        position: relative;
        flex: 1;
        height: 100%;
        margin: 0 8px;
        box-sizing: border-box;
        background-color: rgb(19, 55, 106);

        .title {
          height: 30%;
          font-size: 10px;
          margin: 10px;
          border-bottom: 1px solid rgba(255, 255, 255, 0.3);
        }

        .name {
          height: 70%;
        }

        .normal_light {
          position: absolute;
          top: -5px;
          right: -5px;
          width: 20px;
          height: 20px;
          border-radius: 10px;
          background: url('../img/normal_light.jpg');
          background-size: 100% 100%;
        }

        .abnormal_light {
          position: absolute;
          top: -5px;
          right: -5px;
          width: 20px;
          height: 20px;
          border-radius: 10px;
          background: url('../img/abnormal_light.jpg');
          background-size: 100% 100%;
        }

        .sys_light {
          position: absolute;
          top: -5px;
          right: -5px;
          width: 20px;
          height: 20px;
          border-radius: 10px;
          background: url('../img/sys_light.jpg');
          background-size: 100% 100%;
        }
      }

      .error {
        background-color: #80808080;
      }
    }

    .esb_container {
      display: flex;
      height: 60%;

      .esb {
        width: 100%;
        height: 80px;
        line-height: 80px;
        margin: auto;
        border-radius: 20px;
        background: rgb(19, 55, 106);
        font-size: xx-large;
        text-shadow: 5px 5px 3px black;
      }
    }
  }

  .svg_block {
    position: absolute;
    background: rgba(0, 0, 0, 0);
    left: 0;
    top: 0;
    bottom: 0;
    right: 0;

    .svg_line {
      stroke-dasharray: 10;
      animation: act 5s infinite linear;
    }

    @keyframes act {
      to {
        stroke-dashoffset: -80;
      }
    }
  }
}
</style>

