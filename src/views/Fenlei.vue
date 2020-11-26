<template>
  <!--最外层-->
  <div class="fenleiPage">
    <!-- 头部 -->
    <div class="header">
      <div class="header_left">
        <a href="JD.html"><span class="d"></span></a>
      </div>
      <div class="header_content">
        <div class="header_input">
          <span></span>
          <input
            maxlength="20"
            type="text"
            name=""
            id="mskeyword"
            placeholder="牛仔裤"
            @focus="gosearchkeyword()"
          />
        </div>
      </div>
    </div>

    <!-- 主体 -->
    <div class="body">
      <div class="big">
        <div
          @touchstart="starttouchlist($event)"
          @touchmove="touchmovelist($event)"
          :style="setUstyle"
        >
          <ul id="u1" ref="utest">
            <li
              v-for="(item, index) in category.catetorydata"
              :key="index"
              :class="[category.activeindex == index ? 'active' : '']"
              @click="setcurrent(item.categoryname)"
            >
              {{ item.categoryname }}
            </li>
          </ul>

          <div class="right">
            <div
              v-for="(smallitem, index) in category.currentcategory"
              :key="index"
              style="float: left;margin-bottom: 30px;"
            >
              <span style="font-weight: 600;">{{
                smallitem.smallcategoryname
              }}</span>
              <br />
              <div
                class="right_1"
                v-for="(itemdata, index) in smallitem.smallcategorydetail"
                :key="index"
              >
                <img :src="itemdata.img" style="vertical-align: middle;" />
                <span style="font-size: 12px;">{{ itemdata.text }}</span>
              </div>
            </div>
          </div>
        </div>

        <!--底部-->
        <div class="footer">
          <ul>
            <li>
              <a href="JD.html"><img src="img/1.png"/></a>
            </li>
            <li>
              <a href="#"><img src="img/2.png"/></a>
            </li>
            <li>
              <a href="#"><img src="img/3.png"/></a>
            </li>
            <li>
              <a href="#"><img src="img/4.png"/></a>
            </li>
            <li>
              <a href="Login.html"><img src="img/5.png"/></a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Fenlei",
  data() {
    return {
      category: {
        currentcategory: {}, //当前选择的内容
        catetorydata: [], //总数据列表
        activeindex: 0,
        offsetY: 0,
        ypoint: 0,
        yspace: 0
      }
    };
  },
  methods: {
    starttouchlist: function(e) {
      this.xpoint = e.touches[0].clientY;
    },
    touchmovelist: function(e) {
      var ypoint1 = e.changedTouches[0].clientY;
      //   var pHeight =
      //     document.body.clientHeight || document.documentElement.clientHeight;
      var mHeight = this.category.catetorydata * 46 - 552;
      if (this.yspace >= 1) {
        this.yspace = 0;
      } else if (this.yspace < -mHeight) {
        this.yspace = -mHeight;
      } else {
        this.yspace += ypoint1 - this.ypoint;
      }
      this.ypoint = ypoint1;
    },
    getjson2: function() {
      var self = this;
      axios
        .get("data/cate.json")
        .then(response => {
          if (response.status == 200) {
            self.category.catetorydata = response.data.category;
            self.category.currentcategory =
              response.data.category[0].categorydata;
          }
        })
        .catch(error => {
          console.log(error);
        });
    },

    setcurrent: function(item) {
      for (var i = 0; i < this.category.catetorydata.length; i++) {
        if (item == this.category.catetorydata[i].categoryname) {
          this.category.currentcategory = this.category.catetorydata[
            i
          ].categorydata;
          this.category.activeindex = i;
          this.category.offsetY += -40;
          this.$refs.utest.style.marginTop = this.category.offsetY + "px";
        }
      }
    }
  },
  mounted: function() {
    this.getjson2();
  },
  computed: {
    setUstyle: function() {
      var style = {};
      style.height = this.category.catetorydata * 46 + "px";
      style.marginTop = this.yspace + "px";
      return style;
    },
    changetop: function() {
      var style = {};
      style.marginTop = this.yspace + "px";
      return style;
    }
  }
};
</script>

<style lang="scss">
.fenleiPage {
  /*公共样式*/
  a {
    text-decoration: none;
  }

  /*头部*/
  .d {
    top: 10px;
    background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAYAAABXAvmHAAAABGdBTUEAALGPC/xhBQAAAYpJREFUaAXtmLFOwzAQhhvKE2Rnygu1EhIDezeeho2doRIDG++BhARDNvY8QZX+f6ilArbjs1t0FmcpcWPfnf/v6sinLBbWLAOWAcuAZeA/Z6A5FXzXdSvEuj/E2/R9/3Kq2LE4l7HJ1DmIvxnH8RH2S/o0TfOA7oq/z90uShf4Kb40ntS/CCAgfgcRd1IhufbZACHx2D632P/PuYKkflkv8Yz4rVREib0YQJN4gosAtIkXAWgUnwygVXwSgGbxswDaxUcBahAfBKhFvBcA4lcozJ4wORVmNELbHU7YPz2kvpaO332lBEviKsQTzQcQR1Y26wNgJcmK0rUla32+F25AU3+8VSZdwzC8t237gYc1LgfIfs1xzL9NhkpuvwCoiyJrgfAC1AQRBKgFIgpQA8QsgHaIJADNEMkAWiFEABohxADaILIAEiBeeaLT7tzNlQpZ6+AD1pZlNpy/1U54dh95s+JKnIoAuFAAQqKhyLYY4AjiGv/GJy+MbYpUmbNlwDJgGbAMWAYSM7AH/J4Amlfxzk4AAAAASUVORK5CYII=)
      no-repeat;
    width: 24px;
    height: 24px;
    overflow: hidden;
    display: block;
    position: absolute;
    background-size: 100% auto;
    background-position: 0;
    margin-left: 3vw;
  }
  .header {
    position: fixed;
    top: 0;
    width: 100%;
    height: 44px;
    background-color: white;
    z-index: 999;
  }
  .header_input input {
    border: none;
    outline: none;
    margin: 0 0 0 10px;
    padding-left: 5px;
    margin-top: 8px;
    line-height: 16px;
    white-space: nowrap;
    width: 60%;
    background-color: #f7f7f7;
  }
  .header_content span {
    width: 18px;
    height: 15px;
    display: inline-block;
    background: url(/img/jd-sprites.png) no-repeat;
    background-position: -80px 0;
    background-size: 200px 200px;
    display: inline-block;
    margin-top: 8px;
    margin-left: 5px;
    float: left;
  }
  .header_input {
    float: left;
    width: auto;
  }

  .header_content {
    float: left;
    height: 30px;
    width: calc(100vw - 100px);
    margin: 7px 0 0 15px;
    border-radius: 15px;
    background-color: white;
    overflow: hidden;
    margin-left: 10vw;
    background-color: #f7f7f7;
  }

  .header_right {
    float: left;
    margin: 10px 0 0 10px;
    color: white;
  }

  .header_right a {
    color: white;
  }
  /* 主体 */
  .body {
    width: 100vw;
  }
  .big {
    margin-top: 44px;
    width: 100vw;
    height: 90vh;
  }
  /* 主体左部 */
  #u1 {
    width: 20vw;
    height: 85vh;
    float: left;
    background-color: white;
  }
  #u1 li {
    line-height: 5vh;
    width: 20vw;
  }
  .active {
    background-color: #cbcbcb;
  }
  /* 主体右部 */
  .right {
    width: 79vw;
    height: 85vh;
    float: left;
    margin-left: 1vw;
  }
  .right_1 {
    width: 25vw;
    height: 10vh;
    float: left;
    text-align: center;
    margin-right: 1vw;
  }
  .right_1 img {
    width: 100%;
    height: 100%;
  }
  /*底部*/
  .footer {
    width: 100%;
    height: auto;
    position: fixed;
    bottom: 0;
    left: 0;
    z-index: 999;
    box-shadow: 0 3px 3px 5px #b0b0b0;
    background-color: #b0b0b0;
  }

  .footer ul li {
    justify-content: space-between;
    list-style: none;
    background-color: #fffeee;
    float: left;
    width: 20%;
  }

  .footer img {
    width: 16vw;
  }
}
</style>
