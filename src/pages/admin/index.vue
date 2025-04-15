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
    
    <!-- 热门赛事 -->
    <view class="section-title">
      <text>热门赛事</text>
    </view>
    
    <!-- 赛事列表 -->
    <view class="event-list">
      <!-- 赛事卡片1 -->
      <view class="event-card">
        <view class="event-card-left">
          <image class="event-image" src="/static/images/CompetitionList1.png" mode="aspectFill"></image>
        </view>
        <view class="event-card-right">
          <view class="event-title">粤港澳大湾区大学生创意节</view>
          <view class="event-tags">
            <text class="tag">视频</text>
            <text class="tag">平面</text>
            <text class="tag">策划</text>
            <text class="tag">文案</text>
          </view>
          <view class="event-followers">3279人关注</view>
          <view class="event-status">
            <text class="status-tag status-active">正在征集</text>
            <text class="status-time">剩余12天</text>
          </view>
        </view>
        <view class="bookmark-icon">
          <image src="/static/icons/bookmark-on.png" mode="aspectFit"></image>
        </view>
      </view>
      
      <!-- 赛事卡片2 -->
      <!-- 赛事卡片容器 -->
      <view class="event-card">
        <!-- 赛事卡片左侧区域，包含赛事图片 -->
        <view class="event-card-left">
          <!-- 赛事图片，使用aspectFill模式确保图片填充整个容器 -->
          <image class="event-image" src="/static/images/CompetitionList2.png" mode="aspectFill"></image>
        </view>
        <view class="event-card-right">
          <view class="event-title">大学生创作大赛</view>
          <view class="event-tags">
            <text class="tag">视频</text>
          </view>
          <view class="event-followers">73人关注</view>
          <view class="event-status">
            <text class="status-tag status-active">正在征集</text>
            <text class="status-time">剩余74天</text>
          </view>
        </view>
        <view class="bookmark-icon">
          <image src="/static/icons/bookmark-off.png" mode="aspectFit"></image>
        </view>
      </view>
      
      <!-- 赛事卡片3 -->
      <view class="event-card">
        <view class="event-card-left">
          <image class="event-image" src="/static/images/CompetitionList3.png" mode="aspectFill"></image>
        </view>
        <view class="event-card-right">
          <view class="event-title">赛司光学创意大赛</view>
          <view class="event-tags">
            <text class="tag">平面</text>
            <text class="tag">策划</text>
          </view>
          <view class="event-followers">3279人关注</view>
          <view class="event-status">
            <text class="status-tag status-active">正在评审</text>
            <text class="status-time">将于2023.11.07公布结果</text>
          </view>
        </view>
        <view class="bookmark-icon">
          <image src="/static/icons/bookmark-on.png" mode="aspectFit"></image>
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

// 移除不再需要的跳转函数
/*
const navigateToDetail = (competitionId: string) => {
  console.log('尝试跳转到详情页，ID:', competitionId);
  uni.navigateTo({
    url: `/pages/admin/competition-detail?id=${competitionId}`
  });
};
*/

onMounted(() => {
  console.log('页面加载完成')
})
</script>

<style>
.container {
  min-height: 100vh;
  background-color: #F5F5F5;
  padding-bottom: 30rpx;
}

/* 自定义导航栏 */
/* 自定义导航栏容器样式 */
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

/* 热门赛事标题 */
.section-title {
  font-size: 36rpx;
  font-weight: bold;
  color: #333;
  margin: 30rpx;
}

/* 赛事列表 */
.event-list {
  padding: 0 30rpx;
}

.event-card {
  display: flex;
  background-color: #FFFFFF;
  border-radius: 20rpx;
  padding: 30rpx;
  margin-bottom: 30rpx;
  position: relative;
  box-shadow: 0 2rpx 10rpx rgba(0, 0, 0, 0.05);
}

.event-card-left {
  width: 160rpx;
  height: 160rpx;
  margin-right: 30rpx;
}

.event-image {
  width: 100%;
  height: 100%;
  border-radius: 10rpx;
}

.event-card-right {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.event-title {
  font-size: 32rpx;
  font-weight: bold;
  color: #333;
  margin-bottom: 10rpx;
}

.event-tags {
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

.event-followers {
  font-size: 24rpx;
  color: #999;
  margin-bottom: 10rpx;
}

.event-status {
  display: flex;
  align-items: center;
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

.status-time {
  font-size: 24rpx;
  color: #999;
}

.bookmark-icon {
  position: absolute;
  top: 30rpx;
  right: 30rpx;
  width: 40rpx;
  height: 40rpx;
}

.bookmark-icon image {
  width: 100%;
  height: 100%;
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
