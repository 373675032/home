<template>
  <div class="github-project">
    <div class="title">
      <github-one theme="two-tone" size="24" :fill="['#efefef', '#00000020']" />
      <span>Github</span>
    </div>
    <Swiper
      :modules="[Pagination, Mousewheel]"
      :slides-per-view="1"
      :space-between="40"
      :pagination="{
        el: '.swiper-pagination',
        clickable: true,
        bulletElement: 'div',
      }"
      :mousewheel="true"
    >
      <SwiperSlide v-for="list in projectList" :key="list">
        <el-row class="all-project" :gutter="20">
          <el-col v-for="(item, index) in list" :span="12" :key="index">
            <div class="project cards" @click="toGithub(item)">
              <div class="name">
                <bookmark theme="outline" size="22" fill="#efefef" />
                <div class="name-text">
                  <span class="author">{{ item.author }}</span>
                  <span>{{ item.name }}</span>
                </div>
              </div>
              <span class="desc">{{ item.desc }}</span>
            </div>
          </el-col>
        </el-row>
      </SwiperSlide>
      <div class="swiper-pagination" />
    </Swiper>
  </div>
</template>

<script setup>
import { GithubOne, Bookmark } from "@icon-park/vue-next";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Pagination, Mousewheel } from "swiper";

// 仓库数据
const projectData = [
  {
    name: "xw-fast",
    author: "XUEW",
    desc: "XwFast 是专为 Java Web 开发的基于 Spring 系列框架封装的黑科技脚手架，通过诸多实用工具类/组件的使用，旨在帮助开发者快速、便捷地完成各类开发任务。这些封装的工具组件涵盖了基础增删查改接口、邮件客户端、短信客户端、等一系列操作，可以满足各种不同的开发需求。",
  },
  {
    name: "moti-cloud",
    author: "XUEW",
    desc: "莫提网盘（moti-cloud）是一个基于 SpringBoot 开发的标准 Java Web 项目。存储模式支持 FTP、阿里云 OSS 对象存储。项目选题新颖，完成度较高，前后端不分离的单体架构，非常适合刚刚接触学习 SpringBoot 的技术小白学习。",
  },
  {
    name: "moti-blog",
    author: "XUEW",
    desc: "莫提博客（moti-blog）是一个基于 SpringBoot 开发的标准 Java Web 项目。项目中应用了 SpringBoot、MyBatis、Redis、RabbitMq、ElasticSearch、BootStrap、Thymeleaf 等技术。项目页面美观大气，完成度较高，前后端不分离的单体架构，非常适合刚刚接触学习 SpringBoot 的技术小白学习。",
  },
  {
    name: "molihub",
    author: "XUEW",
    desc: "博客论坛系统（molihub）是一个基于 Spring、SpringMVC、JDBCTemplate、JSP 开发的 Java Web 项目。项目页面美观大气，完成度较高，前后端不分离的单体架构，非常适合刚刚接触学习 Spring 的技术小白学习。",
  },
  {
    name: "su-share",
    author: "XUEW",
    desc: "素材分享网（su-share）是一个基于 SpringBoot 开发的标准 Java Web 项目。项目页面美观大气，完成度较高，前后端不分离的单体架构，集成阿里云 OSS 对象存储素材文件，图片封面上水印，非常适合刚刚接触学习 Spring 的技术小白学习。",
  },
  {
    name: "verio-house",
    author: "XUEW",
    desc: "房屋租赁系统（verio-house）是一个基于 SSM 开发的标准 Java Web 项目。整体页面非常的简约大气，项目的完整度较高。非常适合刚刚接触学习 Spring 的技术小白学习。",
  },
  {
    name: "smart-medicine",
    author: "XUEW",
    desc: "智慧医药系统（smart-medicine）是一个基于 SpringBoot 开发的标准 Java Web 项目。整体页面非常的简约大气，整合了目前非常火爆的 AIGC 生成式 AI（选用的阿里的通义千问大语言模型）技术充当智能医生，以此提升系统的 B 格，整体来看是一个偏向百科查询类的系统，功能设计的较为简单，便于初学者理解和学习。",
  },
  {
    name: "academic-report",
    author: "XUEW",
    desc: "智慧高校学术报告系统（academic-report）是一个基于 SpringBoot 开发的标准 Java Web 项目。系统整体页面设计简约大气，巧妙融合了目前备受瞩目的 AIGC 生成式 AI 技术，选择了阿里通用千问大语言模型，以智能生成趣味报告标题和润色报告内容等方式，提升系统的整体品味。系统涵盖了丰富的 Excel 表格操作功能，支持信息的高效导入和导出。整个系统设计完善，内置了复杂的审核流程，旨在为高校提供一套信息化管理的优质解决方案。",
  },
  {
    name: "kaka-shop",
    author: "XUEW",
    desc: "咖咖商城（kaka-shop）是一个基于 SpringBoot 开发的标准 Java Web 项目。系统整体页面设计简约精美，交互新颖，是一款制作精良的服务于咖啡爱好者的商城系统。",
  },
];

// 计算网站链接
const projectList = computed(() => {
  const result = [];
  for (let i = 0; i < projectData.length; i += 10) {
    const subArr = projectData.slice(i, i + 10);
    result.push(subArr);
  }
  return result;
});

// 跳转至 Github
const toGithub = (data) => {
  window.open(`https://github.com/373675032/${data.name}`);
};
</script>

<style lang="scss" scoped>
.github-project {
  width: 100%;
  margin-top: 20px;
  .title {
    display: flex;
    flex-direction: row;
    align-items: center;
    margin: 0.2rem 0 1.5rem;
    font-size: 1.1rem;
    .i-icon {
      display: flex;
      justify-content: center;
      align-items: center;
      margin-right: 6px;
    }
  }
  .swiper {
    left: -10px;
    width: calc(100% + 20px);
    padding: 5px 10px 0;
    z-index: 0;
    .swiper-slide {
      height: 100%;
    }
    .swiper-pagination {
      position: static;
      margin-top: -8px;
      :deep(.swiper-pagination-bullet) {
        background-color: #fff;
        width: 18px;
        height: 4px;
        border-radius: 4px;
        transition: opacity 0.3s;
        &:hover {
          opacity: 1;
        }
      }
    }
  }
  .all-project {
    width: calc(100% + 20px);
    .project {
      display: flex;
      flex-direction: column;
      justify-content: center;
      margin-bottom: 20px;
      padding: 12px;
      height: 100px;
      background-color: transparent;
      .name {
        display: flex;
        flex-direction: row;
        align-items: center;
        margin-bottom: 8px;
        .i-icon {
          display: flex;
          margin-right: 6px;
        }
        .author {
          opacity: 0.8;
          &::after {
            content: "/";
            margin: 0 4px;
          }
        }
      }
      .desc {
        display: -webkit-box;
        -webkit-box-orient: vertical;
        -webkit-line-clamp: 2;
        overflow: hidden;
        word-break: break-all;
        font-size: 13px;
        opacity: 0.8;
        line-height: 20px;
      }
    }
  }
}
</style>
