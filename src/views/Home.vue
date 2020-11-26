<template>
  <!--最外层-->
  <div class="homePage">
    <!--头部-->
    <div class="header">
      <div class="header_left">
        <span></span>
      </div>
      <div class="header_content">
        <div>
          <span></span>
          <span>|</span>
          <span></span>
        </div>
        <div class="header_input">
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
      <div class="header_right">
        <a
          href="#"
          @click="
            e => {
              e.preventDefault();
              $router.push({ path: 'login' });
            }
          "
          >登录</a
        >
      </div>
    </div>
    <!--主体-->
    <div class="content">
      <div class="floor">
        <!--轮播-->
        <div
          class="lunbo"
          @touchstart="bannerTouchStart($event)"
          @touchend="bannerTouchEnd($event)"
        >
          <ul v-bind:class="banner.cal" v-bind:style="setustyle">
            <li
              class="lunboanser"
              v-for="(item, index) in banner.imgs"
              :key="index"
            >
              <img v-bind:src="item" />
            </li>
          </ul>
        </div>
        <div>
          <ul>
            <li></li>
          </ul>
        </div>
        <!--内容-->
        <div class="floor_all">
          <div class="floor_all_1">
            <div class="floor_1">
              <img src="img/JD03/002.gif" />
              <div class="floor_1_left">
                <img src="img/JD03/04.png" />
              </div>
            </div>
            <div class="floor_2">
              <img src="img/JD03/001.gif" />
            </div>
            <div class="floor_3">
              <img src="img/JD03/003.gif" />
              <div class="floor_3_left">
                <img src="img/JD03/05.png" />
              </div>
            </div>
          </div>
        </div>
        <!--选项栏-->
        <div class="cheak_menu">
          <div class="cheak_menu_1">
            <ul>
              <li>
                <a href="#">
                  <div class="manu_1">
                    <img src="img/JD04/1.png" />
                  </div>
                  <p>京东超市</p>
                </a>
              </li>
              <li>
                <a href="#">
                  <div class="manu_1">
                    <img src="img/JD04/2.png" />
                  </div>
                  <p>数码电器</p>
                </a>
              </li>
              <li>
                <a href="#">
                  <div class="manu_1">
                    <img src="img/JD04/3.png" />
                  </div>
                  <p>京东服饰</p>
                </a>
              </li>
              <li>
                <a href="#">
                  <div class="manu_1">
                    <img src="img/JD04/4.png" />
                  </div>
                  <p>京东生活</p>
                </a>
              </li>
              <li>
                <a href="#">
                  <div class="manu_1">
                    <img src="img/JD04/5.png" />
                  </div>
                  <p>京东到家</p>
                </a>
              </li>
              <li>
                <a href="#">
                  <div class="manu_1">
                    <img src="img/JD04/6.png" />
                  </div>
                  <p>充值缴费</p>
                </a>
              </li>
              <li>
                <a href="#">
                  <div class="manu_1">
                    <img src="img/JD04/7.png" />
                  </div>
                  <p>9.9元拼</p>
                </a>
              </li>
              <li>
                <a href="#">
                  <div class="manu_1">
                    <img src="img/JD04/8.png" />
                  </div>
                  <p>领卷</p>
                </a>
              </li>
              <li>
                <a href="#">
                  <div class="manu_1">
                    <img src="img/JD04/9.png" />
                  </div>
                  <p>领现金</p>
                </a>
              </li>
              <li>
                <a href="#">
                  <div class="manu_1">
                    <img src="img/JD04/10.png" />
                  </div>
                  <p>PLUS会员</p>
                </a>
              </li>
            </ul>
          </div>
        </div>
      </div>
      <!--秒杀框-->
      <div class="miaosha">
        <div class="miaosha_header">
          <div class="floor_seckill">
            <div class="floor_seckill_left">
              <span>京东秒杀</span>
              <span>{{ getsite }}点场</span>
              <div class="floor_ceckill_timr">
                <span>{{ seckilldata.h }}</span>
                <span>{{ seckilldata.m }}</span>
                <span>{{ seckilldata.s }}</span>
              </div>
            </div>
          </div>
        </div>
        <div class="miaosha_body">
          <div
            class="miaosha_body_imgs"
            v-bind:style="setustyle1"
            @touchstart="seckilltouchstart($event)"
            @touchend="seckilltouchmove($event)"
          >
            <ul v-for="(item, index) in seckill.imgs" :key="index">
              <li>
                <div>
                  <a href="#"><img v-bind:src="item"/></a>
                </div>
                <div class="font">
                  <span class="font_1">
                    <em>￥</em>
                    <span>8499</span>
                  </span>
                  <span class="font_2"
                    ><del><em>￥</em> <span>8999</span></del></span
                  >
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
      <!--广告-->
      <div class="gg_photo">
        <div class="gg_photo_left">
          <img src="img/JD06/9c53e25651659d43.png!q70.jpg" />
        </div>
        <div class="gg_photo_right">
          <img src="img/JD06/aba2bcb4855e6e52.png!q70.jpg" />
        </div>
      </div>
      <div class="aaaa">
        <div class="gg_photo_1">
          <img src="img/JD06/下载.webp" />
        </div>
        <div class="gg_photo_2">
          <ul>
            <li>
              <div class="photo_1">
                <img src="img/JD07/1.jpg" />
              </div>
              <div class="gg_photo_2_1">
                <img src="img/JD07/01.jpg" />
              </div>
              <div class="gg_photo_text">
                <p>黄金手镯榜</p>
                <p>13.1万人购买</p>
              </div>
            </li>
            <li>
              <div class="photo_1">
                <img src="img/JD07/2.jpg" />
              </div>
              <div class="gg_photo_2_1">
                <img src="img/JD07/02.jpg" />
              </div>
              <div class="gg_photo_text">
                <p>手提包榜</p>
                <p>13.1万人购买</p>
              </div>
            </li>
            <li>
              <div class="photo_1">
                <img src="img/JD07/3.jpg" />
              </div>
              <div class="gg_photo_2_1">
                <img src="img/JD07/03.jpg" />
              </div>
              <div class="gg_photo_text">
                <p>经典童书</p>
                <p>孩子爱看</p>
              </div>
            </li>
            <li>
              <div class="photo_1">
                <img src="img/JD07/4.jpg" />
              </div>
              <div class="gg_photo_2_1">
                <img src="img/JD07/04.jpg" />
              </div>
              <div class="gg_photo_text">
                <p>超大内存</p>
                <p>内存不爆表</p>
              </div>
            </li>
          </ul>
        </div>
      </div>
      <!--双十一精选会场-->
      <div class="gg_photo_1">
        <img src="img/JD07/aa0285ab7f9a7c8c.png!q70.jpg" />
      </div>
      <div class="elewen_all">
        <!-- 上半部分 -->
        <div
          class="elewen"
          v-bind:style="setustyle2"
          @touchstart="seckilltouchstart($event)"
          @touchend="seckilltouchmove($event)"
        >
          <div class="elewen_1">
            <img src="img/JD08/01.webp" />
            <div class="elewen_1_1">
              <img src="img/JD08/1.webp" />
            </div>
            <div class="elewen_1_1_text">
              <p>无敌电饭煲</p>
            </div>
            <div class="elewen_1_1_text_2">
              <p>爆款降1000</p>
            </div>
          </div>

          <div class="elewen_2">
            <img src="img/JD08/02.webp" />
            <div class="elewen_1_2">
              <img src="img/JD08/2.webp" />
            </div>
            <div class="elewen_1_1_text_3">
              <p>无敌电饭煲</p>
            </div>
            <div class="elewen_1_1_text_4">
              <p>超市万物</p>
            </div>
          </div>

          <div class="elewen_1">
            <img src="img/JD08/01.webp" />
            <div class="elewen_1_1">
              <img src="img/JD08/1.webp" />
            </div>
            <div class="elewen_1_1_text">
              <p>无敌电饭煲</p>
            </div>
            <div class="elewen_1_1_text_2">
              <p>爆款降1000</p>
            </div>
          </div>

          <div class="elewen_2">
            <img src="img/JD08/02.webp" />
            <div class="elewen_1_2">
              <img src="img/JD08/2.webp" />
            </div>
            <div class="elewen_1_1_text_3">
              <p>无敌电饭煲</p>
            </div>
            <div class="elewen_1_1_text_4">
              <p>超市万物</p>
            </div>
          </div>

          <div class="elewen_1">
            <img src="img/JD08/01.webp" />
            <div class="elewen_1_1">
              <img src="img/JD08/1.webp" />
            </div>
            <div class="elewen_1_1_text">
              <p>无敌电饭煲</p>
            </div>
            <div class="elewen_1_1_text_2">
              <p>爆款降1000</p>
            </div>
          </div>

          <div class="elewen_2">
            <img src="img/JD08/02.webp" />
            <div class="elewen_1_2">
              <img src="img/JD08/2.webp" />
            </div>
            <div class="elewen_1_1_text_3">
              <p>无敌电饭煲</p>
            </div>
            <div class="elewen_1_1_text_4">
              <p>超市万物</p>
            </div>
          </div>

          <div class="elewen_1">
            <img src="img/JD08/01.webp" />
            <div class="elewen_1_1">
              <img src="img/JD08/1.webp" />
            </div>
            <div class="elewen_1_1_text">
              <p>无敌电饭煲</p>
            </div>
            <div class="elewen_1_1_text_2">
              <p>爆款降1000</p>
            </div>
          </div>
        </div>
        <!-- 下半部分 -->
        <div
          class="elewen_bottem"
          v-bind:style="setustyle2"
          @touchstart="seckilltouchstart($event)"
          @touchend="seckilltouchmove($event)"
        >
          <div class="elewen_2">
            <img src="img/JD08/02.webp" />
            <div class="elewen_1_2">
              <img src="img/JD08/2.webp" />
            </div>
            <div class="elewen_1_1_text_3">
              <p>无敌电饭煲</p>
            </div>
            <div class="elewen_1_1_text_4">
              <p>超市万物</p>
            </div>
          </div>

          <div class="elewen_1">
            <img src="img/JD08/01.webp" />
            <div class="elewen_1_1">
              <img src="img/JD08/1.webp" />
            </div>
            <div class="elewen_1_1_text">
              <p>无敌电饭煲</p>
            </div>
            <div class="elewen_1_1_text_2">
              <p>爆款降1000</p>
            </div>
          </div>

          <div class="elewen_2">
            <img src="img/JD08/02.webp" />
            <div class="elewen_1_2">
              <img src="img/JD08/2.webp" />
            </div>
            <div class="elewen_1_1_text_3">
              <p>无敌电饭煲</p>
            </div>
            <div class="elewen_1_1_text_4">
              <p>超市万物</p>
            </div>
          </div>

          <div class="elewen_1">
            <img src="img/JD08/01.webp" />
            <div class="elewen_1_1">
              <img src="img/JD08/1.webp" />
            </div>
            <div class="elewen_1_1_text">
              <p>无敌电饭煲</p>
            </div>
            <div class="elewen_1_1_text_2">
              <p>爆款降1000</p>
            </div>
          </div>

          <div class="elewen_2">
            <img src="img/JD08/02.webp" />
            <div class="elewen_1_2">
              <img src="img/JD08/2.webp" />
            </div>
            <div class="elewen_1_1_text_3">
              <p>无敌电饭煲</p>
            </div>
            <div class="elewen_1_1_text_4">
              <p>超市万物</p>
            </div>
          </div>

          <div class="elewen_1">
            <img src="img/JD08/01.webp" />
            <div class="elewen_1_1">
              <img src="img/JD08/1.webp" />
            </div>
            <div class="elewen_1_1_text">
              <p>无敌电饭煲</p>
            </div>
            <div class="elewen_1_1_text_2">
              <p>爆款降1000</p>
            </div>
          </div>

          <div class="elewen_2">
            <img src="img/JD08/02.webp" />
            <div class="elewen_1_2">
              <img src="img/JD08/2.webp" />
            </div>
            <div class="elewen_1_1_text_3">
              <p>无敌电饭煲</p>
            </div>
            <div class="elewen_1_1_text_4">
              <p>超市万物</p>
            </div>
          </div>
        </div>
      </div>

      <div class="djxy">
        <div class="djxy_1">
          <img src="img/JD08/001.jpg" />
        </div>
        <div class="djxy_1">
          <img src="img/JD08/002.jpg" />
        </div>
        <div class="djxy_1">
          <img src="img/JD08/003.jpg" />
        </div>
      </div>
      <!--东家小院-->
      <div class="GJDY">
        <div class="GJDY_1">
          <div class="gg_photo_1">
            <img src="img/JD07/b59f6d8807cfb020.png!q70.jpg" />
          </div>
        </div>
        <div class="GJDY_2">
          <div class="GJDY_2_1">
            <div class="GJDY_2_1_1">
              <span class="graphic-tit">
                排汗减肥
              </span>
              <p>管住嘴迈开腿</p>
            </div>
            <div class="GJDY_2_1_2">
              <img src="img/JD09/1.jpg" />
            </div>
            <div class="GJDY_2_1_2">
              <img src="img/JD09/2.jpg" />
            </div>
          </div>
          <div class="GJDY_2_2">
            <div class="GJDY_2_1">
              <div class="GJDY_2_1_1">
                <span class="graphic-tit">
                  颜值机箱
                </span>
                <p>特色电脑主机机箱</p>
              </div>
              <div class="GJDY_2_1_2">
                <img src="img/JD09/3.jpg" />
              </div>
              <div class="GJDY_2_1_2">
                <img src="img/JD09/4.jpg" />
              </div>
            </div>
          </div>
        </div>
        <div class="GJDY_3">
          <ul>
            <li>
              <div class="GJDY_2_1_1">
                <span class="graphic-tit">
                  减脂瘦身
                </span>
                <p>型男靓女</p>
              </div>
              <div class="GJDY_3_1">
                <img src="img/JD09/5.jpg" />
              </div>
            </li>
            <li>
              <div class="GJDY_2_1_1">
                <span class="graphic-tit">
                  海囤美妆
                </span>
                <p>护肤首选</p>
              </div>
              <div class="GJDY_3_1">
                <img src="img/JD09/6.jpg" />
              </div>
            </li>
            <li>
              <div class="GJDY_2_1_1">
                <span class="graphic-tit">
                  出游系列
                </span>
                <p>旅行穿搭</p>
              </div>
              <div class="GJDY_3_1">
                <img src="img/JD09/7.jpg" />
              </div>
            </li>
            <li>
              <div class="GJDY_2_1_1">
                <span class="graphic-tit">
                  光影世界
                </span>
                <p>时间刻录机</p>
              </div>
              <div class="GJDY_3_1">
                <img src="img/JD09/8.jpg" />
              </div>
            </li>
          </ul>
        </div>
      </div>
      <!--为你推荐-->
      <div class="wntj">
        <div class="gg_photo_1">
          <img src="img/JD07/b59f6d8807cfb020.png!q70.jpg" />
        </div>
        <ul>
          <li>
            <div class="wntj_1">
              <img src="img/JD10/1.webp" />
            </div>
            <div class="wntj_2">
              <span class="wntj_2_1"
                ><img src="img/JD10/001.webp" /><img
                  src="img/JD10/002.webp"
                />华硕（ASUS）RT-AX82U
                双频5400M全千兆路由无线路由器/RGB情境灯效/WiFi6</span
              >
              <p>
                <span class="similar-product-price">
                  ￥<span class="big-price">899</span>
                </span>
                <span class="xiangsi">看相似</span>
              </p>
            </div>
          </li>
          <li>
            <div class="wntj_1">
              <img src="img/JD10/2.webp" />
            </div>
            <div class="wntj_2">
              <span class="wntj_2_1"
                ><img src="img/JD10/001.webp" /><img
                  src="img/JD10/002.webp"
                />华硕（ASUS）RT-AX82U
                双频5400M全千兆路由无线路由器/RGB情境灯效/WiFi6</span
              >
              <p>
                <span class="similar-product-price">
                  ￥<span class="big-price">899</span>
                </span>
                <span class="xiangsi">看相似</span>
              </p>
            </div>
          </li>
        </ul>
        <ul>
          <li>
            <div class="wntj_1">
              <img src="img/JD10/3.webp" />
            </div>
            <div class="wntj_2">
              <span class="wntj_2_1"
                ><img src="img/JD10/001.webp" /><img
                  src="img/JD10/002.webp"
                />华硕（ASUS）RT-AX82U
                双频5400M全千兆路由无线路由器/RGB情境灯效/WiFi6</span
              >
              <p>
                <span class="similar-product-price">
                  ￥<span class="big-price">899</span>
                </span>
                <span class="xiangsi">看相似</span>
              </p>
            </div>
          </li>
          <li>
            <div class="wntj_1">
              <img src="img/JD10/4.webp" />
            </div>
            <div class="wntj_2">
              <span class="wntj_2_1"
                ><img src="img/JD10/001.webp" /><img
                  src="img/JD10/002.webp"
                />华硕（ASUS）RT-AX82U
                双频5400M全千兆路由无线路由器/RGB情境灯效/WiFi6</span
              >
              <p>
                <span class="similar-product-price">
                  ￥<span class="big-price">899</span>
                </span>
                <span class="xiangsi">看相似</span>
              </p>
            </div>
          </li>
        </ul>
        <ul>
          <li>
            <div class="wntj_1">
              <img src="img/JD10/5.webp" />
            </div>
            <div class="wntj_2">
              <span class="wntj_2_1"
                ><img src="img/JD10/001.webp" /><img
                  src="img/JD10/002.webp"
                />华硕（ASUS）RT-AX82U
                双频5400M全千兆路由无线路由器/RGB情境灯效/WiFi6</span
              >
              <p>
                <span class="similar-product-price">
                  ￥<span class="big-price">899</span>
                </span>
                <span class="xiangsi">看相似</span>
              </p>
            </div>
          </li>
          <li>
            <div class="wntj_1">
              <img src="img/JD10/6.webp" />
            </div>
            <div class="wntj_2">
              <span class="wntj_2_1"
                ><img src="img/JD10/001.webp" /><img
                  src="img/JD10/002.webp"
                />华硕（ASUS）RT-AX82U
                双频5400M全千兆路由无线路由器/RGB情境灯效/WiFi6</span
              >
              <p>
                <span class="similar-product-price">
                  ￥<span class="big-price">899</span>
                </span>
                <span class="xiangsi">看相似</span>
              </p>
            </div>
          </li>
        </ul>
        <ul>
          <li>
            <div class="wntj_1">
              <img src="img/JD10/7.webp" />
            </div>
            <div class="wntj_2">
              <span class="wntj_2_1"
                ><img src="img/JD10/001.webp" /><img
                  src="img/JD10/002.webp"
                />华硕（ASUS）RT-AX82U
                双频5400M全千兆路由无线路由器/RGB情境灯效/WiFi6</span
              >
              <p>
                <span class="similar-product-price">
                  ￥<span class="big-price">899</span>
                </span>
                <span class="xiangsi">看相似</span>
              </p>
            </div>
          </li>
          <li>
            <div class="wntj_1">
              <img src="img/JD10/8.webp" />
            </div>
            <div class="wntj_2">
              <span class="wntj_2_1"
                ><img src="img/JD10/001.webp" /><img
                  src="img/JD10/002.webp"
                />华硕（ASUS）RT-AX82U
                双频5400M全千兆路由无线路由器/RGB情境灯效/WiFi6</span
              >
              <p>
                <span class="similar-product-price">
                  ￥<span class="big-price">899</span>
                </span>
                <span class="xiangsi">看相似</span>
              </p>
            </div>
          </li>
        </ul>
        <ul>
          <li>
            <div class="wntj_1">
              <img src="img/JD10/9.webp" />
            </div>
            <div class="wntj_2">
              <span class="wntj_2_1"
                ><img src="img/JD10/001.webp" /><img
                  src="img/JD10/002.webp"
                />华硕（ASUS）RT-AX82U
                双频5400M全千兆路由无线路由器/RGB情境灯效/WiFi6</span
              >
              <p>
                <span class="similar-product-price">
                  ￥<span class="big-price">899</span>
                </span>
                <span class="xiangsi">看相似</span>
              </p>
            </div>
          </li>
          <li>
            <div class="wntj_1">
              <img src="img/JD10/10.webp" />
            </div>
            <div class="wntj_2">
              <span class="wntj_2_1"
                ><img src="img/JD10/001.webp" /><img
                  src="img/JD10/002.webp"
                />华硕（ASUS）RT-AX82U
                双频5400M全千兆路由无线路由器/RGB情境灯效/WiFi6</span
              >
              <p>
                <span class="similar-product-price">
                  ￥<span class="big-price">899</span>
                </span>
                <span class="xiangsi">看相似</span>
              </p>
            </div>
          </li>
        </ul>
        <ul>
          <li>
            <div class="wntj_1">
              <img src="img/JD10/11.webp" />
            </div>
            <div class="wntj_2">
              <span class="wntj_2_1"
                ><img src="img/JD10/001.webp" /><img
                  src="img/JD10/002.webp"
                />华硕（ASUS）RT-AX82U
                双频5400M全千兆路由无线路由器/RGB情境灯效/WiFi6</span
              >
              <p>
                <span class="similar-product-price">
                  ￥<span class="big-price">899</span>
                </span>
                <span class="xiangsi">看相似</span>
              </p>
            </div>
          </li>
          <li>
            <div class="wntj_1">
              <img src="img/JD10/12.webp" />
            </div>
            <div class="wntj_2">
              <span class="wntj_2_1"
                ><img src="img/JD10/001.webp" /><img
                  src="img/JD10/002.webp"
                />华硕（ASUS）RT-AX82U
                双频5400M全千兆路由无线路由器/RGB情境灯效/WiFi6</span
              >
              <p>
                <span class="similar-product-price">
                  ￥<span class="big-price">899</span>
                </span>
                <span class="xiangsi">看相似</span>
              </p>
            </div>
          </li>
        </ul>
      </div>
      <!--底部菜单-->
      <div class="m-common-footer">
        <ul>
          <li>登录</li>
          <li>注册</li>
          <li>客户服务</li>
          <li><a @click="touchup()">返回顶部</a></li>
        </ul>
        <ul>
          <li><img src="img/JD11/1.png" /></li>
          <li><img src="img/JD11/2.png" /></li>
          <li><img src="img/JD11/3.png" /></li>
        </ul>
        <div class="m-common-footer_1">
          Copyright © 2004-2019 京东JD.com 版权所有
        </div>
        <a class="back_to_up" v-if="top" @click="touchup()"></a>
        <!--右边固定栏-->
        <div
          class="right-fixed-jd"
          :class="[rightfixedflag == true ? 'right-fixed-jd-hover' : '']"
        >
          <div class="right-fixed-jd-img">
            <img src="img/JD08/c57d59d388795e4a.png" />
          </div>
          <span>打开京东APP</span>
        </div>
      </div>
      <!--底部-->
      <div class="footer">
        <ul>
          <li>
            <a
              href="JD.html"
              @click="
                e => {
                  e.preventDefault();
                  $router.push({ path: '/' });
                }
              "
              ><img src="img/1.png"
            /></a>
          </li>
          <li>
            <a
              href="fenlei.html"
              @click="
                e => {
                  e.preventDefault();
                  $router.push({ path: 'login' });
                }
              "
              ><img src="img/2.png"
            /></a>
          </li>
          <li>
            <a href="#"><img src="img/3.png"/></a>
          </li>
          <li>
            <a href="#"><img src="img/4.png"/></a>
          </li>
          <li>
            <a
              href="Login.html"
              @click="
                e => {
                  e.preventDefault();
                  $router.push({ path: 'login' });
                }
              "
              ><img src="img/5.png"
            /></a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import $ from "jquery";

const imgbanner = {
  imgs: [
    "img/JD02/05.png",
    "img/JD02/01.png",
    "img/JD02/02.png",
    "img/JD02/03.png",
    "img/JD02/04.png",
    "img/JD02/05.png",
    "img/JD02/01.png"
  ],
  currentindex: 1,
  starttime: null,
  cal: "lunboanser"
};

const srckilldata = {
  imgs: [
    "img/JD05/1.png",
    "img/JD05/2.png",
    "img/JD05/3.png",
    "img/JD05/4.png",
    "img/JD05/5.png",
    "img/JD05/6.png",
    "img/JD05/7.png",
    "img/JD05/8.png",
    "img/JD05/9.png",
    "img/JD05/10.png"
  ],
  xspace: 0,
  xpoint: 0
};

const seckilldata = {
  year: 0,
  month: 0,
  day: 0,
  hour: 0,
  minute: 0,
  second: 0,
  h: 0,
  s: 0,
  m: 0,
  timr: null
};

export default {
  name: "Home",
  data() {
    return {
      banner: imgbanner,
      seckill: srckilldata,
      seckilldata: seckilldata,
      rightfixedflag: false, //固定栏上面的京东
      top: false
    };
  },
  methods: {
    gosearchkeyword: function() {
      var hotword = $("#mskeyword").attr("placeholder");
      localStorage.setItem("hotword", hotword);
      window.location.href = "seach.html";
    },
    bannerTouchStart: function(e) {
      clearInterval(this.banner.timr);
      this.banner.pagex = e.touches[0].clientX;
    },
    bannerTouchEnd: function(e) {
      var self = this;
      var pagex1 = e.changedTouches[0].clientX;
      var pagejj = pagex1 - self.banner.pagex;
      if (pagejj < -100) {
        //向左滑动
        self.banner.cal = "bannertransition";
        self.banner.currentindex++;
        if (self.banner.currentindex >= self.banner.imgs.length - 1) {
          setTimeout(function() {
            self.banner.cal = "";
            self.banner.currentindex = 1;
          }, 1000);
        }
      }
      if (pagejj > 100) {
        //向右滑动
        self.banner.cal = "bannertransition";
        self.banner.currentindex--;
        if (self.banner.currentindex <= 0) {
          setTimeout(function() {
            self.banner.cal = "";
            self.banner.currentindex = self.banner.imgs.length - 2;
          }, 1000);
        }
      }
      //等待手指滑动3秒后重新开始自动切换
      setTimeout(function() {
        self.startbannertime();
      }, 3000);
    },
    // 右滑
    seckilltouchstart: function(e) {
      this.seckill.xpoint = e.touches[0].clientX;
    },
    seckilltouchmove: function(e) {
      var xpoint1 = e.changedTouches[0].clientX;
      var pwidth =
        document.documentElement.clientWidth || document.body.clientWidth;
      var mwidth = ((this.seckill.imgs.length * 16 - 100) * pwidth) / 100 + 10;
      if (this.seckill.xspace >= 5) {
        this.seckill.xspace = 0;
      } else if (this.seckill.xspace < -mwidth) {
        this.seckill.xspace = -mwidth;
      } else {
        this.seckill.xspace += xpoint1 - this.seckill.xpoint;
      }
      this.seckill.xpoint = xpoint1;
    },
    // 置顶
    touchup: function() {
      document.body.scrollTop = document.documentElement.scrollTop = 0;
    },
    touchupanddown: function() {
      var slef = this;
      var starty = 0;
      document.addEventListener(
        "touchstart",
        function(e) {
          starty = e.touches[0].pageY;
        },
        false
      );
      document.addEventListener(
        "touchmove",
        function(e) {
          var endY = e.changedTouches[0].pageY;
          var yspace =
            document.body.scrollTop || document.documentElement.scrollTop;
          var clienty = document.documentElement.clientHeight;

          console.log(clienty + "," + yspace);
          if (starty > endY) {
            //向上
            if (yspace > clienty * 2) {
              slef.top = true;
            }
          }
          if (starty < endY) {
            //向下
            if (yspace < clienty * 2) {
              slef.top = false;
            }
          }
        },
        false
      );
    },
    //轮播定时器
    startbannertime: function() {
      var self = this;
      clearInterval(this.banner.starttime);
      self.banner.starttime = setInterval(function() {
        self.banner.cal = "lunboanser";
        self.banner.currentindex++;
        if (self.banner.currentindex >= self.banner.imgs.length - 1) {
          setTimeout(function() {
            self.banner.cal = "";
            self.banner.currentindex = 1;
          }, 1000);
        }
      }, 3000);
    },
    //倒计时
    startseckilltime: function() {
      clearInterval(this.seckilldata.timr);
      var self = this;
      self.seckilldata.timr = setInterval(function() {
        var nowtime = new Date().getTime(); //得到量秒
        var timrstr =
          self.seckilldata.year +
          "." +
          self.seckilldata.month +
          "." +
          self.seckilldata.day +
          " " +
          (self.seckilldata.hour + 2) +
          ":00:00";
        var aftimer = new Date(timrstr).getTime(); //得到两个小时之后的日期毫秒数
        var sec = (aftimer - nowtime) / 1000;
        var min = sec / 60;
        var hou = min / 60;
        self.seckilldata.h = "0" + parseInt(hou);

        if (parseInt(min % 60) < 10) {
          self.seckilldata.m = "0" + parseInt(min % 60);
        } else {
          self.seckilldata.m = parseInt(min % 60);
        }
        if (parseInt(sec % 60) < 10) {
          self.seckilldata.s = "0" + parseInt(sec % 60);
        } else {
          self.seckilldata.s = parseInt(sec % 60);
        }
      }, 1000);
    }
  },
  mounted: function() {
    this.startbannertime();
    this.touchupanddown();
    //倒计时
    var tim = new Date();
    this.seckilldata.year = tim.getFullYear();
    this.seckilldata.month = tim.getMonth() + 1;
    this.seckilldata.day = tim.getDate();
    this.seckilldata.hour = tim.getHours();
    this.seckilldata.minur1te = tim.getMinutes();
    this.seckilldata.second = tim.getSeconds();
    this.startseckilltime();
    //设置右边固定栏目京东图片的延时隐藏
    var self = this;
    setTimeout(function() {
      self.rightfixedflag = true;
    }, 3000);
  },
  computed: {
    setustyle: function() {
      var style = {};
      style.width = this.banner.imgs.length * 100 + "vw";
      style.marginLeft = -this.banner.currentindex * 100 + "vw";
      return style;
    },
    //倒计时
    getsite: function() {
      var site = this.seckilldata.hour;
      if (this.seckilldata.hour < 10) {
        site = "0" + this.seckilldata.hour;
      }
      return site;
    },
    setustyle1: function() {
      var style = {};
      style.width = this.seckill.imgs.length * 16.6 + "vw";
      style.marginLeft = this.seckill.xspace + "px";
      return style;
    },
    setustyle2: function() {
      var style = {};
      style.width = this.seckill.imgs.length * 16.6 + "vw";
      style.marginLeft = this.seckill.xspace + "px";
      return style;
    }
  }
};
</script>
<style lang="scss">
.homePage {
  /*头部*/
  .header {
    position: fixed;
    top: 0;
    width: 100%;
    height: 44px;
    background-color: rgba(0.5, 0.5, 0.5, 0.1);
    z-index: 999;
  }

  .header_left span {
    float: left;
    background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACgAAAAgAgMAAAAdw9KTAAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAAAMUExURUdwTP///////////waf0AoAAAADdFJOUwDjSYAlncUAAAAbSURBVBjTY5j/Hwq+MdTDmH+RmUgK6AuGhcsAU5tyB6Ji+x0AAAAASUVORK5CYII=)
      no-repeat;
    width: 20px;
    height: 18px;
    margin: 14px 0 0 15px;
    background-size: 100% 100%;
  }

  .header_content {
    float: left;
    height: 30px;
    width: calc(100vw - 100px);
    margin: 7px 0 0 15px;
    border-radius: 15px;
    background-color: white;
    overflow: hidden;
  }

  .header_content span:nth-last-child(1) {
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

  .header_content span:nth-last-child(2) {
    color: #dbdbdb;
    display: inline-block;
    float: left;
    margin: 3px 0 0 0;
  }

  .header_content span:nth-last-child(3) {
    height: 15px;
    width: 20px;
    background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACgAAAAeCAMAAABpA6zvAAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAAAzUExURUdwTOo8Puo7Peo7Pek7Peo7Pe0/Qek7PvE+SP9SUuo7Peo7Peo7Pus8P+o7Peo7Pek7PZSxd20AAAAQdFJOUwBV8eG+hyGkEQbGmWs/rthNA0r+AAAA5klEQVQ4y63T0RaDIAgAUEDRUjP//2u3CI/T1vJhvM3uVBAANGx5xwLgiwSZ3TI6uMYANSyuc7AUs03CUvgHRMTEflcZ76FezDGJTE/wTYNI9whhDePhNxAcDVveQWDJbgK6Y8FPQDBH2WdgPlZmYNQvj5D7tP8Ap4+2s8lQX56g4AK34bGPshJ8gbl/wrXoASOUDanlgvVFB3g2T5sGZ2on9xCp23BJ8tusPVzw7O/zhuxtHSIZDYGRo891WUemjeVZgsu4kmY8ju8Ifb2f/i3WV+/gzq0Zgs0xba0eHCSsj4zLR91f1fAfiWsqzlEAAAAASUVORK5CYII=)
      no-repeat;
    display: inline-block;
    background-size: 100% 100%;
    margin: 8px 5px 0 15px;
    float: left;
  }

  .header_input {
    float: left;
    width: auto;
    width: 60%;
  }

  .header_input input {
    border: none;
    outline: none;
    margin: 0 0 0 10px;
    padding-left: 5px;
    margin-top: 6px;
    line-height: 16px;
    white-space: nowrap;
    width: 60%;
  }

  .header_right {
    float: left;
    margin: 10px 0 0 10px;
    color: white;
  }

  .header_right a {
    color: white;
  }
  /*主体*/
  .content {
    width: 100%;
    height: 100%;
    overflow: hidden;
    position: relative;
    background-color: #fff5ed;
  }

  .floor {
    height: 64vh;
    background-image: url(/img/backgurand.jpg);
    background-repeat: no-repeat;
    background-position: center center;
    background-size: 100% 100%;
    position: relative;
  }

  .lunbo {
    width: 90vw;
    height: 20vh;
    padding-top: 44px;
    background-repeat: no-repeat;
    background-position: center center;
    background-size: 100% 100%;
    margin: 0 auto;
    position: relative;
    overflow: hidden;
  }

  .lunbo ul li {
    width: 100vw;
    height: 20vh;
    float: left;
    text-align: center;
    display: inline-block;
    overflow: hidden;
  }
  .lunbo ul li img {
    width: 92vw;
    border-radius: 5px;
    margin-left: -10vw;
    margin-top: 2vw;
    overflow: hidden;
  }
  .lunboanser {
    transition: all 1s ease-in-out;
  }

  .floor_all {
    width: 100vw;
    height: 15vh;
    float: left;
    margin: 0 auto;
  }

  .floor_1 {
    width: 24.5vw;
    height: 15vh;
    float: left;
    position: relative;
    background: url(/img/JD03/002.gif) no-repeat;
    background-size: 100% 100%;
  }
  .floor_1_left {
    width: 3.5rem;
    height: 3.25rem;
    position: absolute;
    top: 30px;
    left: 20px;
  }
  .floor_2 {
    width: 51vw;
    height: 15vh;
    float: left;
  }
  .floor_3 {
    width: 24.5vw;
    height: 15vh;
    float: left;
    position: relative;
    background: url(/img/JD03/003.gif) no-repeat;
    background-size: 100% 100%;
  }
  .floor_3_left {
    width: 3.5rem;
    height: 3.25rem;
    position: absolute;
    top: 30px;
    right: 20px;
  }
  .floor_all img {
    width: 100%;
    height: 100%;
    display: block;
    overflow: hidden;
  }
  /*选项栏*/
  .cheak_menu {
    width: 100%;
    height: 19vh;
    position: absolute;
    bottom: 0;
    left: 0;
  }
  .cheak_menu_1 {
    width: 96vw;
    height: 20vh;
    background-color: white;
    margin: -5vw auto;
    text-align: center;
    border-radius: 5px;
  }
  .cheak_menu ul li {
    width: 19vw;
    height: 10vh;
    float: left;
    margin-left: 0.1vw;
  }
  .manu_1 {
    width: 18vw;
    height: 7vh;
  }
  .manu_1 img {
    width: 2rem;
    margin-top: 0.5rem;
  }
  .cheak_menu_1 p {
    font-size: 12px;
    color: #b0b0b0;
  }
  /*秒杀框*/
  .miaosha {
    width: 94vw;
    height: 20vh;
    margin: 0 auto;
  }
  .miaosha_header {
    width: 94vw;
    height: 3.5vh;
    background-color: white;
    font-size: 12px;
    margin: 0 auto;
  }
  .floor_seckill {
    width: 100%;
    position: relative;
  }
  .floor_seckill_left {
    width: 100%;
    // background: ;
    height: 1.7rem;
    background-size: contain;
  }
  .floor_ceckill_timr {
    display: inline-block;
  }
  .floor_ceckill_timr span {
    display: inline-block;
    width: 16px;
    height: 16px;
    border-radius: 2px;
    background-color: #fa2c19;
    font-size: 0.7tem;
    color: white;
    font-weight: 400;
    text-align: center;
  }
  .miaosha_body {
    height: 16.5vh;
    background-color: white;
    width: 94vw;
    margin: 0 auto;
    overflow: hidden;
  }
  .miaosha_body_imgs {
    width: 200vw;
  }
  .miaosha_body_imgs ul li {
    width: 3.5rem;
    height: 3.5rem;
    margin-right: 1vw;
  }
  .miaosha_body_imgs ul li img {
    width: 100%;
    height: 100%;
  }
  .font {
    font-size: 12px;
  }
  .font_1 {
    color: #ff0000;
  }
  .font_2 {
    color: #b0b0b0;
  }
  /*广告*/
  .gg_photo {
    width: 94vw;
    height: 20vh;
    margin: 0 auto;
  }
  .gg_photo_left {
    width: 47vw;
    height: 18vh;
    background-color: #fa2c19;
    float: left;
  }
  .gg_photo_left img {
    width: 100%;
    height: 100%;
  }
  .gg_photo_right {
    width: 47vw;
    height: 18vh;
    float: right;
  }
  .gg_photo_right img {
    width: 100%;
    height: 100%;
  }
  .gg_photo_1 {
    width: 98vw;
    height: 5vh;
    margin: 0 auto;
  }
  .gg_photo_1 img {
    width: 100%;
    height: 100%;
  }
  .aaaa {
    width: 100vw;
    height: 20vh;
  }
  .gg_photo_2 {
    width: 100vw;
    height: 20vh;
    margin: 0 auto;
    margin-left: 1rem;
  }
  .gg_photo_2 ul li {
    width: calc(92vw / 4);
    height: auto;
    float: left;
    margin-right: 0.1rem;
    position: relative;
  }
  .photo_1 {
    width: 23vw;
    height: 100%;
  }
  .photo_1 img {
    width: 100%;
    height: 100%;
  }
  .gg_photo_2_1 {
    width: 72%;
    height: 52.5%;
    position: absolute;
    left: 0.7rem;
    top: 0.5rem;
  }
  .gg_photo_2_1 img {
    width: 100%;
    height: 100%;
  }
  .gg_photo_text {
    position: absolute;
    bottom: 0.2rem;
    left: 0.5rem;
  }
  .gg_photo_text p {
    font-size: 12px;
    color: white;
    text-align: center;
  }
  .gg_photo_3 {
    width: 94vw;
    height: 20vh;
    margin: 0 auto;
    background-color: #fa2c19;
    margin-left: -0.1rem;
  }
  .elewen_all {
    width: 200vw;
    height: 25vh;
  }
  .elewen {
    width: 200vw;
    height: 12.5vh;
    margin: 0 auto;
  }
  .elewen_bottem {
    width: 200vw;
    height: 12.5vh;
    margin: 0 auto;
  }
  .elewen_1 {
    width: 20vw;
    height: 10vh;
    float: left;
    position: relative;
    margin-right: 0.5rem;
  }
  .elewen_1 img {
    width: 100%;
    height: 100%;
  }
  .elewen_1_1 {
    width: 16vw;
    height: 7vh;
    position: absolute;
    top: 0.4rem;
    left: 0.5rem;
  }
  .elewen_1_1 img {
    width: 100%;
    height: 100%;
  }
  .elewen_1_1_text {
    width: 20vw;
    height: 2vh;
    background: rgba(0.5, 0.5, 0.5, 0.5);
    max-width: 3.9rem;
    text-overflow: ellipsis;
    overflow: hidden;
    word-break: break-all;
    position: absolute;
    bottom: 1rem;
    left: 0.4rem;
  }
  .elewen_1_1_text p {
    font-size: 1px;
    color: white;
  }
  .elewen_1_1_text_2 {
    width: 20vw;
    font-size: 2px;
    color: white;
    position: absolute;
    bottom: 0.1rem;
    text-align: center;
  }
  .elewen_1_1_text_3 {
    width: 22vw;
    height: 2vh;
    background: rgba(0.5, 0.5, 0.5, 0.5);
    max-width: 3.9rem;
    text-overflow: ellipsis;
    overflow: hidden;
    word-break: break-all;
    position: absolute;
    bottom: 1rem;
    left: 0.4rem;
    font-size: 1px;
    color: white;
  }
  .elewen_1_1_text_4 {
    width: 22vw;
    height: 2vh;
    font-size: 2px;
    color: white;
    position: absolute;
    bottom: 0.1rem;
    text-align: center;
  }
  .elewen_2 {
    width: 22vw;
    height: 11vh;
    float: left;
    position: relative;
    margin-right: 0.5rem;
  }
  .elewen_2 img {
    width: 100%;
    height: 100%;
  }
  .elewen_1_2 {
    width: 18vw;
    height: 8vh;
    position: absolute;
    top: 0.4rem;
    left: 0.5rem;
  }
  .elewen_1_2 img {
    width: 100%;
    height: 100%;
  }
  /*东家小院*/
  .djxy {
    width: 100vw;
    height: 10vh;
    margin-left: 0.1rem;
  }

  .djxy_1 {
    width: calc(99vw / 3);
    height: 10vh;
    float: left;
  }
  .djxy_1 img {
    width: 100%;
    height: 100%;
  }
  .GJDY {
    width: 100vw;
    height: 36vh;
  }
  .GJDY_2 {
    width: 100vw;
    height: 15vh;
  }
  .GJDY_2_1 {
    width: 50vw;
    height: 15vh;
  }
  .graphic-tit {
    font-weight: 700;
    font-size: 0.9rem;
    line-height: 1.125rem;
    display: inline-block;
    max-width: 100%;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
  }
  .GJDY_2_1_1 p {
    font-size: 0.4rem;
  }
  .GJDY_2_1_1 {
    height: 5vh;
  }
  .GJDY_2_1_2 {
    width: 50%;
    height: 10vh;
    float: left;
  }
  .GJDY_2_1_2 img {
    width: 100%;
    height: 100%;
  }
  .GJDY_2_2 {
    width: 50vw;
    height: 15vh;
    float: right;
    margin-top: -15vh;
  }
  .GJDY_3 {
    height: 15vh;
  }
  .GJDY_3 ul li {
    width: 24vw;
    height: 17vh;
    margin-right: 1vw;
  }
  .GJDY_3_1 img {
    width: 100%;
    height: 100%;
  }

  /*底部*/
  .m-common-footer {
    width: 100vw;
    height: 50vh;
  }
  /*为你推荐*/
  .wntj {
    width: 100vw;
    height: 220vh;
  }
  .wntj ul li {
    width: 49vw;
    height: 35vh;
    margin-left: 1vw;
    background-color: white;
    border-radius: 10px;
  }
  .wntj_1 img {
    width: 100%;
    height: 100%;
  }
  .wntj_2_1 {
    box-sizing: border-box;
    height: 35px;
    font-size: 13px;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    word-break: break-all;
    color: #1a1a1a;
    margin-top: 5px;
    line-height: 16px;
    margin-bottom: 3px;
    padding: 0 4px;
  }
  .wntj_2 img {
    width: 16%;
    height: 50%;
  }
  .wntj_2 img:nth-child(2) {
    width: 30%;
    height: 50%;
  }
  .similar-product-price {
    font-size: 12px;
    color: #ff0000;
    font-weight: 300;
  }
  .big-price {
    font-size: 16px;
    font-weight: 500;
    color: #ff0000;
  }
  .xiangsi {
    margin-left: 25vw;
    width: 2vw;
    height: 2vh;
    background-color: #b0b0b0;
    border-radius: 12px;
    font-size: 12px;
  }
  .xiangsi p {
    color: #b0b0b0;
  }
  /*底部菜单*/
  .m-common-footer {
    width: 100vw;
    height: 26vh;
  }
  .m-common-footer ul {
    height: 8vh;
    box-sizing: border-box;
    border-bottom: 1px solid #e5e5e5;
    border-top: 1px solid #e5e5e5;
    padding: 4.26667vw 5.33333vw;
  }
  .m-common-footer ul li {
    float: left;
    text-align: center;
    width: 25%;
    line-height: 5vh;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
    padding: 0 5px;
    box-sizing: border-box;
    color: #848689;
  }
  .m-common-footer ul:nth-child(2) {
    border-bottom: 1px solid #e5e5e5;
    padding: 1.06667vw 2vw;
  }
  .m-common-footer ul:nth-child(2) li {
    float: left;
    text-align: center;
    width: 33.3333%;
  }
  .m-common-footer ul:nth-child(2) li img {
    width: 16vw;
    vertical-align: middle;
  }
  .m-common-footer_1 {
    text-align: center;
    color: #848689;
    font-size: 1.86667vw;
    padding: 2vw 0;
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
  .diandi {
    width: 100vw;
    height: 7vh;
  }
  /*
 * 右边的固定栏
 */
  .right-fixed-jd {
    height: 30px;
    line-height: 30px;
    position: fixed;
    right: 0;
    width: 120px;
    top: 150px;
    z-index: 2000;
    border-radius: 15px 0 0 15px;
    font-size: 0.8rem;
    text-align: center;
    color: white;
    transition: right 1s;
    background-image: linear-gradient(
      135deg,
      rgba(242, 39, 12, 0.9) 0%,
      rgba(242, 39, 12, 0.9) 70%,
      rgba(242, 39, 12, 0.9) 100%
    );
  }
  .right-fixed-jd-hover {
    right: -90px;
  }
  .right-fixed-jd-img {
    float: left;
    height: 26px;
    width: 26px;
    line-height: 26px;
    margin-top: 2px;
  }
  .right-fixed-jd-img img {
    width: 100%;
    height: 100%;
    float: left;
  }
  .right-fixed-jd-img span {
    float: left;
    width: 100px;
    height: 26px;
  }
  /*置顶*/
  .back_to_up {
    position: fixed;
    z-index: 2000;
    bottom: 120px;
    height: 40px;
    width: 40px;
    right: 9px;
    background-image: url("data:image/png;base64,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");
    background-size: 38px 38px;
    background-position: 50%;
    background-repeat: no-repeat;
  }
}
</style>
