<template>
  <view class="container">
    <!-- 自定义导航栏 -->
    <view class="custom-nav">
      <view class="nav-title">
        <text class="title-text">我的队伍</text>
        <text class="title-en">MY TEAMS</text>
      </view>
      <view class="nav-right">
        <image class="nav-icon" src="/static/icons/notification.svg" mode="aspectFit"></image>
      </view>
    </view>
    
    <!-- 搜索框 -->
    <view class="search-box">
      <image class="search-icon" src="/static/icons/search.svg" mode="aspectFit"></image>
      <input class="search-input" type="text" placeholder="搜索队伍..." confirm-type="search" />
    </view>
    
    <!-- 我的队伍列表 -->
    <view class="section-title">
      <text>我的队伍</text>
      <view class="add-team-btn">+ 创建队伍</view>
    </view>
    
    <!-- 队伍列表 -->
    <view class="team-list">
      <!-- 队伍卡片1 -->
      <view class="team-card">
        <view class="team-card-left">
          <image class="team-image" src="/static/images/event1.svg" mode="aspectFill"></image>
        </view>
        <view class="team-card-right">
          <view class="team-title">创意无限队</view>
          <view class="team-info">5人 · 粤港澳大湾区大学生创意节</view>
          <view class="team-status">
            <text class="status-tag status-active">进行中</text>
            <text class="status-time">剩余12天</text>
          </view>
        </view>
      </view>
      
      <!-- 队伍卡片2 -->
      <view class="team-card">
        <view class="team-card-left">
          <image class="team-image" src="/static/images/event2.svg" mode="aspectFill"></image>
        </view>
        <view class="team-card-right">
          <view class="team-title">视觉先锋</view>
          <view class="team-info">3人 · 大学生创作大赛</view>
          <view class="team-status">
            <text class="status-tag status-active">进行中</text>
            <text class="status-time">剩余74天</text>
          </view>
        </view>
      </view>
    </view>
    
    <!-- 推荐队伍 -->
    <view class="section-title">
      <text>推荐队伍</text>
    </view>
    
    <!-- 推荐队伍列表 -->
    <view class="team-list">
      <!-- 推荐队伍卡片 -->
      <view class="team-card">
        <view class="team-card-left">
          <image class="team-image" src="/static/images/event3.svg" mode="aspectFill"></image>
        </view>
        <view class="team-card-right">
          <view class="team-title">光影魔术手</view>
          <view class="team-info">4人 · 赛司光学创意大赛</view>
          <view class="team-status">
            <text class="status-tag status-recruiting">招募中</text>
            <text class="status-time">需要：平面设计、文案</text>
          </view>
          <view class="join-btn">申请加入</view>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

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
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 80rpx 30rpx 20rpx;
  background: linear-gradient(180deg, #4B7BFF 0%, #6B8FFF 100%);
  color: #FFFFFF;
}

.nav-title {
  display: flex;
  flex-direction: column;
}

.title-text {
  font-size: 36rpx;
  font-weight: bold;
  color: #FFFF00;
}

.title-en {
  font-size: 24rpx;
  color: #FFFFFF;
  opacity: 0.8;
}

.nav-icon {
  width: 48rpx;
  height: 48rpx;
}

/* 搜索框 */
.search-box {
  margin: 0 30rpx;
  margin-top: -20rpx;
  height: 80rpx;
  background-color: #FFFFFF;
  border-radius: 40rpx;
  display: flex;
  align-items: center;
  padding: 0 30rpx;
  box-shadow: 0 4rpx 10rpx rgba(0, 0, 0, 0.1);
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

/* 标题栏 */
.section-title {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 36rpx;
  font-weight: bold;
  color: #333;
  margin: 30rpx;
}

.add-team-btn {
  font-size: 28rpx;
  color: #4B7BFF;
  font-weight: normal;
}

/* 队伍列表 */
.team-list {
  padding: 0 30rpx;
}

.team-card {
  display: flex;
  background-color: #FFFFFF;
  border-radius: 20rpx;
  padding: 30rpx;
  margin-bottom: 30rpx;
  position: relative;
  box-shadow: 0 2rpx 10rpx rgba(0, 0, 0, 0.05);
}

.team-card-left {
  width: 120rpx;
  height: 120rpx;
  margin-right: 30rpx;
}

.team-image {
  width: 100%;
  height: 100%;
  border-radius: 10rpx;
}

.team-card-right {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.team-title {
  font-size: 32rpx;
  font-weight: bold;
  color: #333;
  margin-bottom: 10rpx;
}

.team-info {
  font-size: 26rpx;
  color: #666;
  margin-bottom: 10rpx;
}

.team-status {
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

.status-time {
  font-size: 24rpx;
  color: #999;
}

.join-btn {
  align-self: flex-start;
  font-size: 26rpx;
  color: #FFFFFF;
  background-color: #4B7BFF;
  padding: 8rpx 20rpx;
  border-radius: 30rpx;
}
</style>