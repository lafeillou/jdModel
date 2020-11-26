<template>
  <div class="searchPage">
    <div class="seach_hotword_header">
      <a href="JD.html"></a>
      <div class="seach_hotword_input">
        <i class="fa fa-search"></i>
        <input
          type="text"
          id="mskeyword"
          :placeholder="searchkeyword.dfkeyword"
        />
      </div>
      <button id="btnsearch">搜索</button>
    </div>
    <div class="seach_hotword_content">
      <div class="seach_hotword_content_visble">
        <p>热门搜索</p>
        <span v-if="searchkeyword.visible" @click="sethotkeyshow()">显示</span>
        <span v-else @click="sethotkeyshow()">隐藏</span>
      </div>
      <div class="seach_hotword_content_hidden" v-if="searchkeyword.visible">
        已隐藏搜索发现
      </div>
      <div class="seach_hotword_txt" v-else>
        <span v-for="(item, index) in getrandhotkey" :key="index">
          <a
            href="#"
            :class="[index >= 0 && index < 3 ? 'seach_hotword_top3' : '']"
            >{{ item }}</a
          >
        </span>
      </div>
    </div>
  </div>
</template>

<script>
const hotkeycontainer = {
  hotkeycontent: [
    "洗碗机家用",
    "拼装模型",
    "蜡烛香薰",
    "豆浆机",
    "进口牛奶",
    "不粘锅煎锅",
    "破壁器",
    "汽车坐垫",
    "不锈钢蒸锅",
    "电话手表",
    "自拍杆",
    "白板",
    "游戏本",
    "电脑椅",
    "跑步机",
    "游戏显卡",
    "微波炉",
    "羽毛球拍",
    "开关插座"
  ],
  visible: false,
  dfkeyword: ""
};

export default {
  data() {
    return { searchkeyword: hotkeycontainer };
  },
  methods: {
    sethotkeyshow: function() {
      this.searchkeyword.visible = !this.searchkeyword.visible;
    }
  },
  computed: {
    getrandhotkey: function() {
      var randkey = [];
      var arrlength = this.searchkeyword.hotkeycontent.length;
      for (var i = 0; i < 12; i++) {
        var randindex = Math.floor(Math.random() * arrlength);
        if (!randkey.includes(this.searchkeyword.hotkeycontent[randindex])) {
          randkey.push(this.searchkeyword.hotkeycontent[randindex]);
        }
        if (randkey.length == 12) {
          break;
        } else {
          i--;
        }
      }
      return randkey;
    }
  },
  mounted: function() {
    this.searchkeyword.dfkeyword = localStorage.getItem("hotword");
  }
};
</script>

<style lang="scss">
.searchPage {
  a {
    text-decoration: none;
    color: #737373;
    font-size: 0.6rem;
  }

  .seach_hotword_header {
    width: 100%;
    height: 44px;
    position: relative;
    text-align: center;
    border-bottom: 1px solid #e2e2e2;
  }
  .seach_hotword_header a {
    display: inline-block;
    float: left;
    height: 44px;
    width: 8vw;
    background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACgAAAAoBAMAAAB+0KVeAAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAAAhUExURUdwTF1famFhal1fal1fal5ga39/f15hbF5ga2JidV1fasLnCw4AAAAKdFJOUwDxN13aWgVemg1awhgkAAAATUlEQVQoz2NgGAjA5FiAKai4SgxToRQWQcVVqwKwKFyMTaHBUFTI4IVFIeeqVQ0MRKnEGkAg25cyEGc9VocOCqUBxKUQrGkJe6qjEgAAfcYsJDT7oy4AAAAASUVORK5CYII=)
      no-repeat;
    background-size: 20px 20px;
    margin-top: 12px;
  }
  .seach_hotword_header .seach_hotword_input {
    float: left;
    height: 30px;
    width: 73vw;
    line-height: 30px;
    background-color: #e2e2e2;
    border-radius: 15px;
    margin-top: 7px;
  }
  .seach_hotword_input i {
    display: inline-block;
    float: left;
    margin-left: 10px;
    height: 30px;
    line-height: 30px;
    color: #b0b0b0;
  }
  .seach_hotword_input input {
    float: left;
    margin-top: 4px;
    margin-left: 15px;
    height: 20px;
    line-height: 20px;
    width: 55vw;
    border: none;
    outline: none;
    vertical-align: bottom;
    background-color: #e2e2e2;
  }
  .seach_hotword_header button {
    float: left;
    height: 30px;
    width: 12vw;
    border: none;
    background-color: #e93b3d;
    border-radius: 5px;
    color: white;
    margin-left: 2.5vw;
    margin-top: 5px;
  }
  .seach_hotword_content {
    width: 95%;
    position: relative;
    margin: 0 auto;
  }
  .seach_hotword_content .seach_hotword_content_visble {
    width: 100%;
    height: 40px;
    margin-top: 10px;
  }
  .seach_hotword_content_visble p {
    float: left;
    font-size: 0.8rem;
    margin-left: 5px;
    margin-top: 0px;
  }
  .seach_hotword_content_visble span {
    float: right;
    font-size: 0.8rem;
    margin-right: 5px;
    color: #b0b0b0;
  }
  .seach_hotword_txt {
    width: 100%;
    text-align: center;
  }
  .seach_hotword_txt span {
    float: left;
    font-size: 0.6rem;
    height: 23px;
    padding-left: 10px;
    padding-right: 10px;
    padding-top: 10px;
    background-color: #e2e2e2;
    margin: 0px 8px 5px 5px;
    border-radius: 5px;
  }
  .seach_hotword_content_hidden {
    width: 100%;
    height: 30vw;
    line-height: 30vw;
    color: #b0b0b0;
    text-align: center;
    font-size: 0.8rem;
  }
  .seach_hotword_top3 {
    color: #e93b3d;
  }
}
</style>
