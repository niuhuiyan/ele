<template>
  <div id="wai">
    <div class="personal-wrap">
      <div class="personal-head">
        <img
          src="data:image/png;base64,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"
          class="head-img"
        />
        <dl>
          <dt>OoQRPrvXHisc</dt>
          <dd>177****7822</dd>
        </dl>
      </div>
      <ul class="personal-menu">
        <li>
          我的优惠
          <span class="hongbao-tip" style="display: none;">0个红包</span>
        </li>
        <li>收货地址</li>
        <li>我的客服</li>
        <li>规则中心</li>
      </ul>
      <!---->
      <div class="quit">退出登录</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "eleBuyMine"
};
</script>

<style scoped>
#wai {
  flex: 1;
}
.personal-wrap {
    padding-bottom: 0.53333rem;
}
.personal-wrap .personal-head {
    background: #0097ff;
    padding: 1.25rem;
    position: relative;
    height: 3.75rem;
    font-size: .75rem;
}
.personal-wrap .personal-head .head-img {
    width: 3.75rem;
    height: 3.75rem;
    border-radius: 50%;
    float: left;
}
.personal-wrap .personal-head dl {
    margin: 0 0 0 4.6875rem;
    color: #fff;
}
.personal-wrap .personal-head dl dt {
    font-size: 1.3125rem;
    margin-top: .5rem;
    font-weight: normal;
}
.personal-wrap .personal-head dl dd {
    margin: 0;
    font-size: .75rem;
    margin-top: .3125rem;
}
.personal-wrap .personal-menu {
    padding-left: 1.25rem;
    background: #fff;
}
.personal-wrap .personal-menu li {
    height:2.875rem;
    line-height: 2.875rem;
    font-size: 1rem;
    position: relative;
    border-bottom: 1px solid #f1f1f1;
    padding-left: 1.5625rem;
}
.personal-wrap .personal-menu li:last-child {
    border: 0;
}
.personal-wrap .quit {
    height: 2.9365rem;
    line-height: 2.9365rem;
    color: #ff5339;
    font-size: 1.0625rem;
    text-align: center;
    background: #fff;
    margin-top: .375rem;
}
</style>
