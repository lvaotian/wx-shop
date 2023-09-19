<script setup lang="ts">
import type { BannerItem } from '@/types/home'
import CustomNavbar from './components/CustomNavbar.vue'
import CategoryPanel from './components/CategoryPanel.vue'
import { getHomeBannerAPI } from '@/services/home'
import { ref } from 'vue'
import { onLoad } from '@dcloudio/uni-app'
// 获取轮播图数据
const bannerList = ref<BannerItem[]>([])
const getHomeBannerData = async () => {
  const res = await getHomeBannerAPI()
  bannerList.value = res.result
}
onLoad(() => {
  getHomeBannerData()
})
</script>

<template>
  <view class="index">
    <!-- 自定义导航栏 -->
    <CustomNavbar />
    <!-- 自定义轮播图 -->
    <XtxSwiper :list="bannerList" />
    <CategoryPanel />
  </view>
</template>

<style lang="scss">
//
</style>
