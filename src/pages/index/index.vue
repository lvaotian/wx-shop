<script setup lang="ts">
import type { BannerItem, CategoryItem } from '@/types/home'
import CustomNavbar from './components/CustomNavbar.vue'
import CategoryPanel from './components/CategoryPanel.vue'
import { getHomeBannerAPI, getHomeCategoryAPI } from '@/services/home'
import { ref } from 'vue'
import { onLoad } from '@dcloudio/uni-app'
// 获取轮播图数据
const bannerList = ref<BannerItem[]>([])
const getHomeBannerData = async () => {
  const res = await getHomeBannerAPI()
  bannerList.value = res.result
}
// 获取前台分类数据
const categoryList = ref<CategoryItem[]>([])
const getHomeCategoryData = async () => {
  const res = await getHomeCategoryAPI()
  categoryList.value = res.result
}
onLoad(() => {
  getHomeBannerData()
  getHomeCategoryData()
})
</script>

<template>
  <view class="index">
    <!-- 自定义导航栏 -->
    <CustomNavbar />
    <!-- 自定义轮播图 -->
    <XtxSwiper :list="bannerList" />
    <CategoryPanel :list="categoryList" />
  </view>
</template>

<style lang="scss">
//
page {
  background-color: #f7f7f7;
}
</style>
