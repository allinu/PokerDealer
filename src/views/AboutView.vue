<template>
  <div class="bg">
  </div>
  <div class="container">
    <img class="logo" src="@/assets/logo.png" alt="logo">
    <p>PokerDealer (发牌手) 出自<a href="https://www.smartisan.com/"><img src="@/assets/smartisan.png"
          alt="smartisan" />锤子科技</a>TNT 工作站发布会，一次搜索可以同时返回多个搜索引擎的搜索结果。</p>
    <div class="comment">
      <p>smartisan 标识和 Smarisan Compact CNS 字体归 smartisan.com 所有</p>
      <p>本网站logo为网站作者自行绘制，所有权归作者(<a href="https://github.com/allinu">allinu</a>)所有</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.bg {
  background: url("@/assets/bg.jpg") repeat center;
  height: calc(100vh - 50px);
  width: 100vw;
  filter: blur(150px);
  position: absolute;
  z-index: -99;
}

.container {
  width: 100vw;
  height: calc(100vh - 250px);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-sizing: border-box;

  img.logo {
    height: 200px;
  }


  >p {
    margin-top: 30px;
    font-size: 20px;
    line-height: 20px;


    a {
      position: relative;
      padding: 0 10px 0 24px;
      background: rgba(255, 255, 255, 0.2);
      border-radius: 10px;

      &:hover {
        background: rgba(255, 255, 255, 0.8);
      }

      img {
        height: 20px;
        position: absolute;
        left: 2px;
        background: #fff;
        border-radius: 50%;
      }
    }
  }

  .comment {
    font-size: 12px;
    text-align: center;
    position: fixed;
    bottom: 10px;
  }
}
</style>
