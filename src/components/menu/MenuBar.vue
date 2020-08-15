<template>
  <ul class="menu-bar">
        <li>
            <i class="ico-cate"></i>
            <p>商品分类</p>
        </li>
        <li class="btn-center">
            <i class="ico-post"></i>
            <p>发布商品</p>
        </li>
        <li>
            <i class="ico-folder"></i>
            <p>批量管理</p>
        </li>
    </ul>
</template>

<script>
export default {
    name: 'Menu'
}
</script>

<style lang="scss">
@import "../../assets/scss/rem";
.menu-bar {
    position: fixed;
    left: 0;
    right: 0;
    bottom: 0;
    height: rem(102);
    border-top: rem(1) solid #ebebeb;
    text-align: center;
    &:before {
        width: rem(80);
        height: rem(80);
        border-radius: 50%;
        border: rem(1) solid #ebebeb;
        position: absolute;
        z-index: -1;
        content: '';
        top: rem(-20);
        left: 50%;
        margin-left: rem(-40);
        background: #fff;
    }
    &:after {
        position: absolute;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        z-index: 1;
        background: #fff;
        content: '';
    }
    li {
        display: inline-block;
        vertical-align: bottom;
        position: relative;
        z-index: 2;
        width: rem(108);
        margin: 0 rem(60);
        font-size: rem(20);
        color: #808080;
    }
    i {
        background: url("/img/spr.png");
        background-size: $sprSize;
        display: block;
        margin: 0 auto;
    }
    .ico-cate {
        height:rem(39);
        width:rem(40);
        background-position:0 rem(-291);
    }
    .ico-post {
        height:rem(76);
        width:rem(76);
        background-position:rem(-76) rem(-204);
    }
    .ico-folder {
        height:rem(36);
        width:rem(40);
        background-position:0 rem(-254);
    }
    p {
        margin-top: rem(4);
    }
    .btn-center {
        margin-top: rem(-11);
    }
}
</style>