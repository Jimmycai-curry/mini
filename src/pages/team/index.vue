<template>
  <view class="container">
    <!-- 自定义导航栏 -->
    <view class="custom-nav">
      <image src="/static/images/bg_top.png" mode="aspectFill" class="nav-bg-image"></image>
      
      <!-- 搜索区域 -->
      <view class="search-area">
        <view class="search-box">
          <image class="search-icon" src="/static/icons/search.svg" mode="aspectFit"></image>
          <input class="search-input" type="text" placeholder="寻找比赛/活动/企业..." confirm-type="search" />
        </view>
        <view class="nav-right">
          <image class="nav-icon" src="/static/icons/notification-off.png" mode="aspectFit"></image>
        </view>
      </view>
    </view>

    <!-- 轮播图 -->
    <swiper class="banner-swiper" indicator-dots indicator-color="rgba(255, 255, 255, 0.6)" indicator-active-color="#FFFFFF" autoplay interval="3000" circular>
      <swiper-item>
        <image class="banner-image" src="/static/images/competition1.png" mode="aspectFill"></image>
      </swiper-item>
      <swiper-item>
        <image class="banner-image" src="/static/images/competition2.png" mode="aspectFill"></image>
      </swiper-item>
      <swiper-item>
        <image class="banner-image" src="/static/images/competition3.png" mode="aspectFill"></image>
      </swiper-item>
      <swiper-item>
        <image class="banner-image" src="/static/images/competition4.png" mode="aspectFill"></image>
      </swiper-item>
    </swiper>
    
    <!-- 选项卡导航 -->
    <view class="tab-bar">
      <view 
        class="tab-item" 
        :class="{ 'active': activeTab === 'support' }" 
        @click="activeTab = 'support'"
      >
        <text>支持单位</text>
      </view>
      <view 
        class="tab-item" 
        :class="{ 'active': activeTab === 'partner' }" 
        @click="activeTab = 'partner'"
      >
        <text>合作单位</text>
      </view>
      <view 
        class="tab-item" 
        :class="{ 'active': activeTab === 'creative' }" 
        @click="activeTab = 'creative'"
      >
        <text>创意公司</text>
      </view>
    </view>
    
    <!-- 支持单位列表 -->
    <view v-if="activeTab === 'support'" class="company-list">
      <!-- 公司卡片1 -->
      <view class="company-card">
        <view class="company-card-left">
          <image class="company-image" src="/static/images/CompetitionList1.png" mode="aspectFill"></image>
        </view>
        <view class="company-card-right">
          <view class="company-title">蓝色光标Blue Digital</view>
          <view class="company-tags">
            <text class="tag">广告</text>
            <text class="tag">传媒</text>
            <text class="tag">公关</text>
            <text class="tag">展览</text>
          </view>
          <view class="company-desc">蓝色光标(数字)致力于提供专业的数字技术、数据、资源和服务能力，为客户提供整合的智能营销解决方案，集聚零售、出海营销、品牌营销...</view>
          <view class="company-status">
            <text class="status-tag status-recruiting">招聘中</text>
          </view>
        </view>
      </view>
    </view>
    
    <!-- 合作单位列表 -->
    <view v-if="activeTab === 'partner'" class="company-list">
      <!-- 公司卡片 -->
      <view class="company-card">
        <view class="company-card-left">
          <image class="company-image" src="/static/images/CompetitionList2.png" mode="aspectFill"></image>
        </view>
        <view class="company-card-right">
          <view class="company-title">原象i2mago</view>
          <view class="company-tags">
            <text class="tag">设计</text>
            <text class="tag">传媒</text>
          </view>
          <view class="company-desc">数字营业创意公司，成立于2006年，总部位于广州，在北京设有分公司。我们是一家专注品牌建设与整合型数字营销机构，我们擅长为...</view>
        </view>
      </view>
    </view>
    
    <!-- 创意公司列表 -->
    <view v-if="activeTab === 'creative'" class="company-list">
      <!-- 公司卡片 -->
      <view class="company-card">
        <view class="company-card-left">
          <image class="company-image" src="/static/images/CompetitionList3.png" mode="aspectFill"></image>
        </view>
        <view class="company-card-right">
          <view class="company-title">蓝狮科技Lancest</view>
          <view class="company-tags">
            <text class="tag">广告</text>
            <text class="tag">传媒</text>
            <text class="tag">公关</text>
          </view>
          <view class="company-desc">蓝狮科技，专注于电子商务事业，依托多品牌体系化运营能力，全业务数字化支撑能力，引领中国品牌走向世界。</view>
          <view class="company-status">
            <text class="status-tag status-recruiting">招聘中</text>
          </view>
        </view>
      </view>
    </view>
    
    <!-- 底部提示图片 -->
    <view class="list-bottom">
      <image src="/static/images/list_bottom.png" mode="aspectFit" class="bottom-image"></image>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

// 定义当前激活的选项卡，默认显示支持单位
const activeTab = ref('support')

onMounted(() => {
  console.log('队伍页面加载完成')
})
</script>

<style>
.container {
  min-height: 100vh;
  background-color: #F5F5F5;
  padding-bottom: 30rpx;
}

/* 自定义导航栏 */
.custom-nav {
  position: relative;
  width: 100%;
  height: 300rpx; /* 设置固定高度 */
  padding: 0;
  overflow: hidden;
}

/* 导航栏背景图片 */
.nav-bg-image {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 0; /* 确保图片在底层 */
  object-fit: cover; /* 确保图片完全覆盖容器 */
}

.nav-icon {
  width: 48rpx;
  height: 48rpx;
}

/* 搜索区域 */
.search-area {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 0 30rpx;
  position: absolute;
  bottom: 25rpx;
  left: 0;
  right: 0;
  z-index: 1; /* 确保搜索区域在背景图上方 */
}

/* 搜索框 */
.search-box {
  flex: 1;
  height: 60rpx;
  background-color: #FFFFFF;
  border-radius: 40rpx;
  display: flex;
  align-items: center;
  padding: 0 30rpx;
  box-shadow: 0 4rpx 10rpx rgba(0, 0, 0, 0.1);
  margin-right: 20rpx;
}

.search-icon {
  width: 40rpx;
  height: 40rpx;
  margin-right: 20rpx;
}

.search-input {
  flex: 1;
  height: 80rpx;
  font-size: 28rpx;
  color: #333;
}

.nav-right {
  display: flex;
  align-items: center;
}

/* 轮播图 */
.banner-swiper {
  margin: 30rpx;
  height: 300rpx;
  border-radius: 20rpx;
  overflow: hidden;
}

.banner-image {
  width: 100%;
  height: 100%;
  border-radius: 20rpx;
}

/* 选项卡导航 */
.tab-bar {
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin: 20rpx 30rpx;
  position: relative;
}

.tab-item {
  flex: 1;
  text-align: center;
  font-size: 32rpx;
  color: #666;
  padding: 16rpx 0;
  position: relative;
  transition: all 0.3s;
}

.tab-item.active {
  color: #333;
  font-weight: bold;
}

.tab-item.active::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 40rpx;
  height: 6rpx;
  background-color: #4F7DF7;
  border-radius: 3rpx;
}

/* 公司列表 */
.company-list {
  padding: 0 30rpx;
}

.company-card {
  display: flex;
  background-color: #FFFFFF;
  border-radius: 20rpx;
  padding: 30rpx;
  margin-bottom: 30rpx;
  position: relative;
  box-shadow: 0 2rpx 10rpx rgba(0, 0, 0, 0.05);
}

.company-card-left {
  width: 120rpx;
  height: 120rpx;
  margin-right: 30rpx;
}

.company-image {
  width: 100%;
  height: 100%;
  border-radius: 10rpx;
}

.company-card-right {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.company-title {
  font-size: 32rpx;
  font-weight: bold;
  color: #333;
  margin-bottom: 10rpx;
}

.company-tags {
  display: flex;
  flex-wrap: wrap;
  margin-bottom: 10rpx;
}

.tag {
  font-size: 24rpx;
  color: #666;
  background-color: #F5F5F5;
  padding: 4rpx 16rpx;
  border-radius: 20rpx;
  margin-right: 10rpx;
  margin-bottom: 10rpx;
}

.company-desc {
  font-size: 26rpx;
  color: #666;
  margin-bottom: 10rpx;
  line-height: 1.4;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}

.company-status {
  display: flex;
  align-items: center;
  margin-bottom: 10rpx;
}

.status-tag {
  font-size: 24rpx;
  padding: 4rpx 16rpx;
  border-radius: 6rpx;
  margin-right: 20rpx;
}

.status-active {
  background-color: #E6F7FF;
  color: #1890FF;
}

.status-recruiting {
  background-color: #F6FFED;
  color: #52C41A;
}
/* 底部提示图片 */
.list-bottom {
  display: flex;
  justify-content: center;
  padding: 30rpx 0 50rpx;
}

.bottom-image {
  width: 100%;
  height: 250rpx;
}
</style>