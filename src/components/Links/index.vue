<template>
  <div class="links">
    <div class="line">
      <Icon size="20">
        <Link />
      </Icon>
      <span class="title">网站列表</span>
    </div>
    <el-row class="link-all" :gutter="20">
      <el-col
        :span="8"
        v-for="(item, index) in linksData"
        :key="item"
        @click="jumpLink(item.link)"
      >
        <div
          class="item cards"
          :style="index < 3 ? 'margin-bottom: 20px' : null"
        >
          <Icon size="26">
            <component :is="item.icon" />
          </Icon>
          <span class="name">{{ item.name }}</span>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { Icon } from "@vicons/utils";
import {
  Cloud,
  Fire,
  CameraRetro,
  ItunesNote,
  Search,
  BookOpen,
} from "@vicons/fa";

// 网站链接数据
// 建议不要超出6个，若需要超出请自行调整样式
let linksData = [
  {
    icon: Cloud,
    name: "群晖",
    link: "https://nas.0830.tech:8100/",
  },
  {
    icon: CameraRetro,
    name: "相册",
    link: "https://nas.0830.tech:9200",
  },
  {
    icon: ItunesNote,
    name: "音乐",
    link: "https://nas.0830.tech:9300/",
  },
  {
    icon: Search,
    name: "搜搜",
    link: "https://nav.0830.tech/",
  },
  {
    icon: BookOpen,
    name: "博客",
    link: "https://wp.0830.tech:9900",
  },
  {
    icon: Fire,
    name: "今日热榜",
    link: "https://hot.0830.tech/",
  },
];

// 链接跳转
const jumpLink = (url) => {
  window.open(url, "_blank");
};
</script>

<style lang="scss" scoped>
.links {
  .line {
    margin: 2rem 0.25rem 1rem;
    font-size: 1.1rem;
    display: flex;
    align-items: center;
    animation: fade;
    -webkit-animation: fade 0.5s;
    .title {
      margin-left: 8px;
      font-size: 1.15rem;
      text-shadow: 0 0 5px #00000050;
    }
  }
  .link-all {
    .item {
      height: 100px;
      width: 100%;
      display: flex;
      align-items: center;
      flex-direction: row;
      justify-content: center;
      animation: fade;
      -webkit-animation: fade 0.5s;

      &:hover {
        transform: scale(1.02);
        background: rgb(0 0 0 / 40%);
        transition: 0.3s;
      }
      .name {
        font-size: 1.1rem;
        margin-left: 8px;
      }
      @media (min-width: 720px) and (max-width: 820px) {
        .name {
          display: none;
        }
      }
      @media (max-width: 720px) {
        height: 80px;
      }
      @media (max-width: 460px) {
        flex-direction: column;
        .name {
          font-size: 1rem;
          margin-left: 0;
          margin-top: 8px;
        }
      }
    }
  }
}
</style>
