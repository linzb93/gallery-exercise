<template>
  <li :class="{
      'set-top': setTop
  }">
    <div class="date-txt one-line" v-if="setTop">置顶</div>
    <div class="date-txt" v-else>
        <p class="day">{{day}}</p>
        <p class="month">{{month}}月</p>
    </div>
    <div class="item-main">
      <div class="goods-line clearfix">
        <div class="goods-img fl">
          <img :src="cover" alt="" />
        </div>
        <div class="info fl">
          <h3>
            <span class="price" v-if="price">￥{{price}}</span>
            {{title}}
          </h3>
          <p class="status">
            <span v-if="status.shareTime">{{shareTime}} 已分享</span>
            <span v-if="status.editTime">{{editTime}} 已编辑</span>
            <span v-if="status.locked" class="lock">私密</span>
          </p>
        </div>
      </div>
      <div class="goods-ctrl-bar clearfix">
        <div class="ctrl-left fl">
          <a :class="{
              'btn-attr': true,
              on: goodsAttrVisible
            }" href="javascript:;" title @click="toggleGoodsAttrVisible">商品属性</a>
          <a class="other-btn" href="javascript:;" title>编辑</a>
          <a class="other-btn" href="javascript:;" title>下载</a>
          <a class="other-btn" v-if="canBuy" href="javascript:;" title>购买</a>
        </div>
        <a class="btn-share fr" href="javascript:;" title>分享</a>
      </div>
      <div :class="{
          'goods-attr-con': true,
          on: goodsAttrVisible
      }">
        <dl>
          <dt>货号：</dt>
          <dd>{{goodsAttr.num}}</dd>
        </dl>
        <dl>
          <dt>规格：</dt>
          <dd>
            <span v-for="item in goodsAttr.specs" :key="item">{{item}}</span>
          </dd>
        </dl>
        <dl>
          <dt>型号：</dt>
          <dd>
            <span v-for="type in goodsAttr.types" :key="type">{{type}}</span>
          </dd>
        </dl>
      </div>
    </div>
  </li>
</template>

<script>
export default {
    name: 'GoodsItem',
    props: {
        title: { // 标题
            type: String,
            required: true
        },
        setTop: { // 是否置顶
            type: Boolean,
            required: true
        },
        date: { // 日期
            type: String,
            required: true
        },
        price: { // 价格
            type: Number
        },
        cover: { // 封面图
            type: String,
            required: true
        },
        status: { // 状态（已分享时间、已编辑时间等）
            type: Object,
            required: true
        },
        canBuy: { // 能否购买
            type: Boolean,
            required: true
        },
        goodsAttr: { // 产品属性（货号、规格、型号）
            type: Object,
            required: true
        }
    },
    data() {
        return {
            goodsAttrVisible: false // 是否显示产品属性
        };
    },
    computed: {
        month() {
            return this.date.split('.')[1];
        },
        day() {
            return this.date.split('.')[2];
        },
        shareTime() {
            // 已分享时间
            return this.status.shareTime && this.status.shareTime.split('.').slice(1).join('.');
        },
        editTime() {
            // 已编辑时间
            return this.status.editTime && this.status.editTime.split('.').slice(1).join('.');
        }
    },
    methods: {
        // 切换产品属性显示
        toggleGoodsAttrVisible() {
            this.goodsAttrVisible = !this.goodsAttrVisible;
        }
    }
};
</script>

<style lang="scss">
@import "../../assets/scss/mixin";
@import "../../assets/scss/rem";

.goods-list {
    padding-bottom: rem(90);
    li {
        background: #fff;
        padding-left: rem(90);
        position: relative;
        &:after {
            position: absolute;
            bottom: 0;
            left: rem(80);
            right: rem(40);
            height: 0;
            content: '';
            border-bottom: rem(1) solid #ededed;
        }
        &.set-top {
            background: #f7f7ff;
        }
    }
    .date-txt {
        position: absolute;
        width: rem(50);
        left: rem(30);
        top: rem(18);
        color: #333;
        font-weight: bold;
        &:after {
            @include tri('right', rem(8), #333);
            content: '';
            position: absolute;
            right: rem(0);
            top: rem(50);
        }
        &.one-line {
            width: rem(70);
            left: rem(10);
            font-size: rem(30);
            &:after {
                top: rem(12);
            }
        }
    }
    .month {
        font-size: rem(20);
    }
    .day {
        font-size: rem(30);
    }
    .item-main {
        
        padding: rem(18) 0 rem(16);
    }
    .goods-img {
        width: rem(156);
        height: rem(156);
        img {
            width: 100%;
            height: 100%;
        }
    }
    .info {
        margin-left: rem(20);
        width: rem(455);
    }
    h3 {
        font-size: rem(26);
        color: #333;
        height: rem(78);
        font-weight: normal;
        display: -webkit-box;
        overflow: hidden;
        -webkit-line-clamp: 2;
        -webkit-box-orient: vertical;
        span {
            display: inline-block;
            vertical-align: middle;
            height: rem(34);
            line-height: rem(34);
            width: rem(84);
            text-align: center;
            border-radius: rem(6);
            background: #ebebff;
            font-size: rem(26);
            color: #333;
        }
    }
    .status {
        margin-top: rem(30);
        font-size: rem(22);
        color: #999;
        span {
            margin-right: rem(25);
            &:last-child {
                margin-right: 0;
            }
        }
        .lock {
            position: relative;
            &:before {
                content: '';
                display: inline-block;
                vertical-align: middle;
                margin: rem(-2) rem(6) 0 0;
                height:rem(20);
                width:rem(14);
                background: url("/img/spr.png");
                background-size: $sprSize;
            }
        }
    }
    .goods-ctrl-bar {
        margin: rem(24) rem(35) 0 0;
    }
    .ctrl-left {
        margin-top: rem(14);
    }
    .btn-attr {
        font-size: rem(24);
        color: #999;
        margin-right: rem(56);
        width: rem(120);
        display: inline-block;
        &.on {
            &:before {
                @include tri('bottom', rem(8), #999);
            }
        }
        &:before {
            @include tri('right', rem(8), #999);
            content: '';
            display: inline-block;
            vertical-align: middle;
            margin-right: rem(8);
            margin-top: rem(-3);
        }
    }
    .other-btn {
        font-size: rem(24);
        color: #7c75da;
        margin-right: rem(66);
        &:last-child {
            margin-right: 0;
        }
    }
    .btn-share {
        width: rem(110);
        height: rem(55);
        border-radius: rem(28);
        color: #fff;
        text-align: center;
        line-height: rem(55);
        font-size: rem(24);
        letter-spacing: rem(4);
        text-indent: rem(4);
        background-image: linear-gradient(to left, #7f7dd9, #8993d8);
    }
}
.goods-attr-con {
    margin: rem(20) rem(35) 0 0;
    color: #999;
    display: none;
    font-size: rem(20);
    &.on {
        display: block;
    }
    dl {
        position: relative;
        padding-left: rem(70);
        margin-bottom: rem(5);
        &:last-child {
            margin-bottom: 0;
        }
    }
    dt {
        position: absolute;
        left: 0;
        top: rem(2);
    }
    span {
        min-width: rem(46);
        padding: 0 rem(5);
        height: rem(24);
        line-height: rem(24);
        border-radius: rem(12);
        text-align: center;
        font-size: rem(18);
        vertical-align: middle;
        display: inline-block;
        margin: 0 rem(9) rem(9) 0;
        border: rem(1) solid #999;
    }
}
</style>