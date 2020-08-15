<template>
  <div class="top-con">
    <i class="ico-back fl"></i>
    <h1>我的相册</h1>
    <a class="btn-share fr" href="javascript:;" title>
      <i></i>
      <span>分享</span>
    </a>
  </div>
</template>

<script>
export default {
	name: "NavBar"
};
</script>

<style lang="scss">
@import "../../assets/scss/rem";
header {
  .top-con {
		height: rem(86);
		padding-top: rem(40);
		position: fixed;
		left: 0;
		top: 0;
		width: 100%;
		z-index: 3;
		background: url(/img/header-bg.jpg) center top no-repeat;
    background-size: rem(750) rem(400);
    h1 {
      font-size: rem(36);
      color: #fff;
      font-weight: normal;
      text-align: center;
      line-height: rem(86);
    }
  }
  .ico-back {
		background: url("/img/spr.png") 0 rem(-20);
		background-size: $sprSize;
    height: rem(32);
    width: rem(20);
    margin: rem(27) 0 0 rem(24);
    position: absolute;
    left: 0;
    top: rem(40);
  }
  .btn-share {
    position: absolute;
    right: rem(24);
    top: rem(60);
    i {
      display: inline-block;
      vertical-align: middle;
      height: rem(32);
      width: rem(32);
			background: url("/img/spr.png") 0 rem(-184);
			background-size: $sprSize;
      margin-right: rem(10);
    }
    span {
      vertical-align: middle;
      font-size: rem(28);
      color: #fff;
    }
  }
}
</style>