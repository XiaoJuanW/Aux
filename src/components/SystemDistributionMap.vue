<template>
  <!-- 系统分块图 -->
  <div class="distribution_map_container">
    <div class="title_box">
      <div class="all_num">1941411</div>
      <div class="title_box">
        <div class="title">业务系统图</div>
        <div class="subtitle">product pic</div>
      </div>
    </div>
    <div class="distribution_map_content">
      <div class="top_wrapper">
        <div v-for="(item, index) in top" :class="(item.status == -1) ? 'service_block error': 'service_block'">
          <div class="title">
            <span class="title_sys">{{item.sys}}</span>
            <span class="title_num">{{item.num}}</span>
          </div>
          <div class="name">
            <div class="title_name"> {{item.name}} </div>
          </div>
          <!-- <div :class="(item.status == 1) ? 'normal_light' : (item.status == -1 ? 'abnormal_light' : 'sys_light')"></div> -->
        </div>
      </div>
      <div class="esb_container">
        <div class="esb" id="esb">ESB</div>
      </div>
      <div class="bottom_wrapper">
        <div v-for="(item, index) in bottom" :class="(item.status == -1) ? 'service_block error': 'service_block'">
          <div class="title">
            <span class="title_sys">{{item.sys}}</span>
            <span class="title_num">{{item.num}}</span>
          </div>
          <div class="name">
            <div class="title_name"> {{item.name}} </div>
          </div>
          <!-- <div :class="(item.status == 1) ? 'normal_light' : (item.status == -1 ? 'abnormal_light' : 'sys_light')"></div> -->
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
      html += '<path class="path" stroke="' + lineColor + '" stroke-width="3" d="M ' + x + ' ' + y + ' ' + x + ' ' + toY + '" />';
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
      html2 += '<path class="path" stroke="' + lineColor2 + '" stroke-width="3" d="M ' + x2 + ' ' + y2 + ' ' + x2 + ' ' + toY2 + '" />';
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
      top: [{ sys: '集团', num: 12, name: 'OA', status: 1 },  // status 1正常  -1异常  0系统 
      { sys: '集团', num: 1, name: 'MDM', status: -1 },
      { sys: '集团', num: 4, name: 'FSSC', status: 0 },
      { sys: '集团', num: 2, name: 'HR', status: -1 },
      { sys: '电力', num: 6, name: 'FIS', status: 1 },
      { sys: '电力', num: 9, name: 'PLM', status: 1 }],
      bottom: [{ sys: '家电', num: 14, name: 'PDM', status: -1 },
      { sys: '家电', num: 11, name: 'OMS', status: 1 },
      { sys: '家电', num: 10, name: 'IMS', status: 1 },
      { sys: '家电', num: 9, name: 'SRM', status: 0 },
      { sys: '家电', num: 2, name: 'SAP', status: -1 },
      { sys: '医疗', num: 2, name: 'HIS', status: -1 }]
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

  .title_box {
    position: relative;
    width: 100%;
    height: 50px;

    .all_num {
      font-size: 40px;
      font-weight: 900;
      color: rgb(232, 102, 43);
    }

    .title_box {
      position: absolute;
      top: 5px;
      right: 0;
      text-align: right;

      .title {
        font-size: 14px;
        color: #ddd;
      }

      .subtitle {
        font-size: 12px;
        color: #998e00;
      }
    }
  }

  .distribution_map_content {
    width: 100%;
    height: calc(100% - 50px);

    .top_wrapper, .bottom_wrapper {
      display: flex;
      height: 60px;

      .service_block {
        position: relative;
        flex: 1;
        height: 100%;
        margin: 0 2px;
        padding: 3px;
        background-color: rgba(33, 97, 241, 0.4);

        .title {
          display: flex;
          height: 40%;
          font-size: 10px;
          box-sizing: border-box;
          border-bottom: 1px solid rgba(255, 255, 255, 0.3);

          .title_sys {
            height: 15px;
            line-height: 15px;
            margin: auto;
            width: 70%;
            text-align: left;
          }

          .title_num {
            height: 15px;
            line-height: 15px;
            margin: auto;
            width: 30%;
            text-align: right;
          }
        }

        .name {
          display: flex;
          height: 60%;

          .title_name {
            width: 100%;
            height: 20px;
            line-height: 20px;
            margin: auto;
          }
        }
      }

      .error {
        background-color: rgba(128, 128, 128, 0.4);
      }
    }

    .esb_container {
      display: flex;
      height: calc(100% - 120px); // 容器高度 - top_wrapper - bottom_wrapper

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

