<script setup lang="ts">
import { ref, computed, reactive, watch, onMounted, onUpdated } from 'vue';

interface Engine {
  id: number,
  name: string,
  base: string,
  url: string,
  enable: boolean
}
interface EngineList {
  data: Array<Engine>
}

const searchContent = ref("")
const active = ref(false)
const engineList: EngineList = reactive({
  data: [
    {
      id: 1,
      name: "夸克",
      base: "https://quark.sm.cn/s?q=%s&by=submit&snum=1",
      url: "",
      enable: true
    },
    {
      id: 2,
      name: "搜狗",
      base: "https://m.sogou.com/web/searchList.jsp?keyword=%s",
      url: "",
      enable: true
    },
    {
      id: 3,
      name: "微博",
      base: "https://m.weibo.cn/search?containerid=100103type%3D1%26q%3D%s",
      url: "",
      enable: true
    },
    {
      id: 4,
      name: "京东",
      base: "https://so.m.jd.com/ware/search.action?keyword=%s&searchFrom=home&sf=11&as=1",
      url: "",
      enable: true
    },
    {
      id: 5,
      name: "淘宝",
      base: "https://main.m.taobao.com/search/index.html?pageType=3&q=%s",
      url: "",
      enable: true
    },
    {
      id: 6,
      name: "头条",
      base: "https://so.toutiao.com/search/?keyword=%s&pd=synthesis&source=input&traffic_source=&original_source=&in_tfs=&in_ogs=",
      url: "",
      enable: true
    },
    {
      id: 7,
      name: "微信",
      base: "https://weixin.sogou.com/weixinwap?type=2&ie=utf8&_sug_=n&_sug_type_=&s_from=input&query=%s",
      url: "",
      enable: true
    }
  ]
})

watch(searchContent, (newValue, oldValue) => {
  if (newValue == "") {
    active.value = false
  }
})

function submitValue() {
  active.value = true
  for (const engine of engineList.data) {
    engine.url = engine.base.replace(/%s/, searchContent.value)
  }
}

</script>

<template>
  <div class="bg">
  </div>
  <div class="out">
    <div class="container">
      <div class="search" :class="{ active: active && searchContent }">
        <input type="text" autofocus v-model="searchContent" placeholder="输入内容，回车搜索" @keyup.enter="submitValue">
      </div>
      <div class="results" v-show="active && searchContent">
        <div class="result" v-for="engine in engineList.data" :key="engine.id" v-show="engine.enable">
          <div class="engine-name">{{ engine.name }}</div>
          <iframe :src="engine.url" frameborder="0"></iframe>
        </div>
      </div>
    </div>
  </div>
  <p class="copyright">本网站logo为网站作者自行绘制，所有权归作者(<a href="https://github.com/allinu">allinu</a>)所有</p>
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
.copyright{
  width: 100%;
  height: 30px;
  line-height: 30px;
  font-size: 14px;
  position: fixed;
  bottom: 0;
  text-align: center;
}

.out {
  height: calc(100vh - 50px);
  align-items: center;
  padding: 0 20px;

  .container {
    margin: 0 auto;

    .search {
      position: absolute;
      top: 40%;
      left: 50%;
      margin-left: -250px;
      transition: all .1s;

      &.active {
        top: 11px;
        left: 50%;
        margin-left: -250px;
        input {
          font-size: 16px;
        }
      }

      input {
        height: 30px;
        width: 500px;
        box-sizing: border-box;
        border: 2px dashed #000;
        border-radius: 5px;
        padding: 0 5px;
        background: transparent;
        outline: none;
        font-family: SCM;
        font-size: 20px;
      }

    }

    .results {
      display: flex;
      flex-direction: row;
      overflow-x: scroll;
      transition: all 1s;
      padding-top: 18px;

      .result {
        height: calc(100vh - 110px);
        width: 350px;
        min-width: 350px;
        margin-left: 20px;
        border-radius: 5px;
        overflow-y: scroll;

        &:first-child {
          margin-left: 0;
        }

        .engine-name {
          height: 40px;
          line-height: 40px;
          font-family: SCM;
          font-size: 18px;
          font-weight: bold;
          box-sizing: border-box;
          color: #000;
          padding-left: 10px;
        }

        iframe {
          box-sizing: border-box;
          height: calc(100% - 42px);
          width: 100%;
          border-radius: 5px;
          background: #fff;
          color: #000;

          * {
            font-family: SCR;
          }
        }
      }
    }
  }

}
</style>