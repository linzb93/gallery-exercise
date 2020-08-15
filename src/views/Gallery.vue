<template>
  <div>
    <header>
      <nav-bar title="我的相册" />
      <div class="user-con">
        <div class="first-con clearfix">
          <div class="user-info fl">
            <div class="avatar">
              <div class="avatar-img">
                <img :src="avatar" alt />
              </div>
              <i class="ico-vip svip"></i>
            </div>
            <span class="username">{{username}}</span>
          </div>
          <a class="mini-prog fr" href="javascript:;" title>
            <i></i>
            <span>小程序</span>
          </a>
        </div>
        <ul class="data-con">
          <li>
            <span class="label">上新</span>
            <span class="num">{{data.newest}}</span>
          </li>
          <li>
            <span class="label">全部</span>
            <span class="num">{{data.total}}</span>
          </li>
          <li>
            <span class="label">人气</span>
            <span class="num">{{data.popular}}</span>
          </li>
        </ul>
      </div>
    </header>
    <div class="main">
        <ul class="menu">
            <li>
                <a href="javascript:;" title="">图集</a>
            </li>
            <li>
                <a class="on" href="javascript:;" title="">全部</a>
            </li>
            <li>
                <a href="javascript:;" title="">视频</a>
            </li>
        </ul>
        <div class="ctrl-bar clearfix">
            <div class="search-bar fl">
                <i class="ico-search"></i>
                <input type="text" placeholder="请输入关键词">
                <span class="split"></span>
                <i class="ico-pic"></i>
            </div>
            <div class="ctrl-right fr">
                <a class="btn-order fl" href="javascript:;" title=""></a>
                <a class="btn-filter fl" href="javascript:;" title=""><i></i>筛选</a>
            </div>
        </div>
        <div class="goods-list">
            <ul>
                <goods-item
                    v-for="item in goods"
                    :key="item.id"
                    :title="item.title"
                    :setTop="item.setTop"
                    :date="item.date"
                    :price="item.price"
                    :cover="item.cover"
                    :status="item.status"
                    :canBuy="item.canBuy"
                    :goodsAttr="item.attr"
                />
            </ul>
            <p class="bottom-txt">没有更多啦~</p>
        </div>
    </div>
    <a class="btn-to-top"  href="javascript:;" title="" @click="goodsGalleryToTop">
        <i></i>
        <p>TOP</p>
    </a>
    <menu-bar />
  </div>
</template>

<script>
import axios from 'axios';
import NavBar from '@/components/header/NavBar.vue';
import GoodsItem from './components/GoodsItem.vue';
import MenuBar from '@/components/menu/MenuBar.vue';

export default {
  name: 'Gallery',
  components: {
    NavBar,
    GoodsItem,
    MenuBar
  },
  data() {
    return {
        avatar: '', // 头像
        username: '', // 用户名
        data: {
            total:0,
            newest: 0,
            popular: 0
        }, // 统计数据
        goods: [] // 商品列表
    };
  },
  mounted() {
      axios.get('/data/goods.json')
      .then(res => {
          const {data} = res;
          this.avatar = data.avatar;
          this.username = data.username;
          this.data = data.stats;
          this.goods = data.goods;
      });
  },
  methods: {
      // 点击返回顶部
      goodsGalleryToTop() {
          window.scrollTo(0,0);
      }
  }
};
</script>

<style lang="scss">
@import "../assets/scss/rem";
header {
    height: rem(399);
    padding-top: rem(1);
    .user-con {
        margin-top: rem(125);
        padding-top: rem(36);
        height: rem(238);
        background: url(/img/header-bg.jpg) center top no-repeat;
        background-size: rem(750) rem(400);
    }
    .user-info {
        margin-left: rem(28);
    }
    .avatar {
        position: relative;
        display: inline-block;
        vertical-align: middle;
        width: rem(110);
        height: rem(110);
    }
    .avatar-img {
        width: 100%;
        height: 100%;
        border-radius: 50%;
        overflow: hidden;
        img {
            width: 100%;
            height: 100%;
        }
    }
    .ico-vip {
        position: absolute;
        right: rem(-8);
        bottom: 0;
        height:rem(25);
        width:rem(49);
        background: url("/img/spr.png");
        background-size: $sprSize;
    }
    .svip {
        background-position: 0 rem(-354);
    }
    .username {
        vertical-align: middle;
        margin-left: rem(14);
        font-size: rem(32);
        color: #fff;
    }
    .mini-prog {
        height:rem(76);
        width:rem(157);
        background: url("/img/spr.png") 0 rem(-494);
        background-size: $sprSize;
        margin-top: rem(16);
        i {
            float: left;
            height:rem(18);
            width:rem(21);
            background: url("/img/spr.png") 0 rem(-52);
            background-size: $sprSize;
            margin: rem(32) 0 0 rem(24);
        }
        span {
            color: #fff;
            font-size: rem(24);
            float: left;
            margin: rem(23) 0 0 rem(8);
        }
    }
    .data-con {
        margin-top: rem(65);
        li {
            line-height: 1;
            border-left: rem(1) solid rgba(255,255,255,0.3);
            padding: 0 rem(35);
            font-size: rem(24);
            color: #fff;
            display: inline-block;
            &:first-child {
                border-left: 0;
            }
        }
        .label {
            margin-right: rem(8);
        }
        .num {
            font-weight: bold;
        }
    }
}
.main {
    .menu {
        background: #fff;
        border-bottom: rem(1) solid #ebebeb;
        height: rem(90);
        line-height: rem(90);
        padding: 0 rem(86);
        &:after {
            content: '';
            width: 100%;
            display: inline-block;
            height: 0;
            overflow: hidden;
        }
        li {
            display: inline-block;
            vertical-align: middle;
            text-align: center;
            margin-left: rem(193);
            &:first-child {
                margin-left: 0;
            }
        }
        a {
            display: block;
            font-size: rem(30);
            position: relative;
            color: #333;
            &.on {
                font-weight: bold;
                &:after {
                    content: '';
                    position: absolute;
                    bottom: 0;
                    left: 0;
                    right: 0;
                    height: rem(5);
                    border-radius: rem(3);
                    background-image: linear-gradient(to left, #7f7dd9, #8992d8);
                }
            }
        }
    }
    .ctrl-bar {
        background: #fff;
        padding: rem(28) rem(25) rem(25) rem(20);
    }
    .search-bar {
        width: rem(490);
        height: rem(60);
        line-height: rem(60);
        border-radius: rem(30);
        background: #f2f2f2;
        input {
            width: rem(300);
            height: 100%;
            margin-left: rem(10);
            font-size: rem(28);
            color: #333;
            background: none;
            outline: none;
            border:0;
            vertical-align: middle;
        }
        .split {
            width: 0;
            height: rem(30);
            border-right: rem(1) solid #999;
            display: inline-block;
            vertical-align: middle;
            margin: 0 rem(30) 0 rem(10);
        }
    }
    .ico-search {
        margin-left: rem(34);
        height:rem(26);
        width:rem(27);
        background: url("/img/spr.png") 0 rem(-98);
        background-size: $sprSize;
        display: inline-block;
        vertical-align: middle;
    }
    .ico-pic {
        height:rem(39);
        width:rem(39);
        background: url("/img/spr.png") 0 rem(-216);
        background-size: $sprSize;
        display: inline-block;
        vertical-align: middle;
    }
    .ctrl-right {
        margin-top: rem(5);
    }
    .btn-order {
        height:rem(28);
        width:rem(28);
        background: url("/img/spr.png") 0 rem(-125);
        background-size: $sprSize;
        margin: rem(6) rem(35) 0 0;
    }
    .btn-filter {
        position: relative;
        font-size: rem(28);
        color: #333;
        &:before {
            content: '';
            position: absolute;
            top: 0;
            bottom: 0;
            left: rem(-11);
            width: rem(1);
            background: #999;
        }
        i {
            height:rem(26);
            width:rem(26);
            background: url("/img/spr.png") 0 rem(-71);
            background-size: $sprSize;
            display: inline-block;
            vertical-align: middle;
            margin: 0 rem(5) 0 rem(13);
        }
        span {
            vertical-align: middle;
            color: #333;
        }
    }
}
.btn-to-top {
    position: fixed;
    right: rem(20);
    bottom: rem(320);
    width: rem(98);
    height: rem(98);
    border: rem(1) solid #999;
    border-radius: 50%;
    background: #fff;
    i {
        display: block;
        margin: rem(20) auto 0;
        height:rem(22);
        width:rem(44);
        background: url("/img/spr.png") 0 rem(-331);
        background-size: $sprSize;
    }
    p {
        margin-top: rem(4);
        text-align: center;
        font-size: rem(28);
        color: #b2b2b2;
    }
}
.bottom-txt {
    text-align: center;
    margin-top: rem(36);
    font-size: rem(24);
    color: #999;
    padding-bottom: rem(30);
}
</style>