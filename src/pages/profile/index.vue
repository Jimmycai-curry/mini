<template>
  <view class="container">
    <!-- 自定义导航栏 -->
    <view class="custom-nav">
      <view class="nav-title">
        <text class="title-text">个人中心</text>
        <text class="title-en">MY PROFILE</text>
      </view>
      <view class="nav-right">
        <image class="nav-icon" src="/static/icons/notification.svg" mode="aspectFit"></image>
      </view>
    </view>
    
    <!-- 用户信息卡片 -->
    <view class="user-card">
      <view class="user-info">
        <image class="user-avatar" src="/static/logo.png" mode="aspectFill"></image>
        <view class="user-details">
          <view class="user-name">用户名</view>
          <view class="user-school">某某大学</view>
        </view>
      </view>
      <view class="edit-profile-btn">编辑资料</view>
    </view>
    
    <!-- 用户数据统计 -->
    <view class="user-stats">
      <view class="stat-item">
        <view class="stat-number">5</view>
        <view class="stat-label">参与比赛</view>
      </view>
      <view class="stat-item">
        <view class="stat-number">2</view>
        <view class="stat-label">获奖次数</view>
      </view>
      <view class="stat-item">
        <view class="stat-number">3</view>
        <view class="stat-label">我的队伍</view>
      </view>
    </view>
    
    <!-- 功能菜单 -->
    <view class="menu-list">
      <view class="menu-group">
        <view class="menu-item">
          <view class="menu-icon competition"></view>
          <view class="menu-text">我的比赛</view>
          <view class="menu-arrow">></view>
        </view>
        <view class="menu-item">
          <view class="menu-icon team"></view>
          <view class="menu-text">我的队伍</view>
          <view class="menu-arrow">></view>
        </view>
        <view class="menu-item">
          <view class="menu-icon works"></view>
          <view class="menu-text">我的作品</view>
          <view class="menu-arrow">></view>
        </view>
      </view>
      
      <view class="menu-group">
        <view class="menu-item">
          <view class="menu-icon favorite"></view>
          <view class="menu-text">我的收藏</view>
          <view class="menu-arrow">></view>
        </view>
        <view class="menu-item">
          <view class="menu-icon history"></view>
          <view class="menu-text">浏览历史</view>
          <view class="menu-arrow">></view>
        </view>
      </view>
      
      <view class="menu-group">
        <view class="menu-item">
          <view class="menu-icon settings"></view>
          <view class="menu-text">设置</view>
          <view class="menu-arrow">></view>
        </view>
        <view class="menu-item">
          <view class="menu-icon feedback"></view>
          <view class="menu-text">意见反馈</view>
          <view class="menu-arrow">></view>
        </view>
        <view class="menu-item">
          <view class="menu-icon about"></view>
          <view class="menu-text">关于我们</view>
          <view class="menu-arrow">></view>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

onMounted(() => {
  console.log('个人中心页面加载完成')
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

/* 用户信息卡片 */
.user-card {
  margin: 30rpx;
  background-color: #FFFFFF;
  border-radius: 20rpx;
  padding: 30rpx;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 2rpx 10rpx rgba(0, 0, 0, 0.05);
}

.user-info {
  display: flex;
  align-items: center;
}

.user-avatar {
  width: 120rpx;
  height: 120rpx;
  border-radius: 60rpx;
  margin-right: 20rpx;
}

.user-name {
  font-size: 32rpx;
  font-weight: bold;
  color: #333;
  margin-bottom: 10rpx;
}

.user-school {
  font-size: 26rpx;
  color: #666;
}

.edit-profile-btn {
  font-size: 26rpx;
  color: #4B7BFF;
  padding: 10rpx 20rpx;
  border: 1px solid #4B7BFF;
  border-radius: 30rpx;
}

/* 用户数据统计 */
.user-stats {
  margin: 0 30rpx 30rpx;
  background-color: #FFFFFF;
  border-radius: 20rpx;
  display: flex;
  justify-content: space-around;
  padding: 30rpx 0;
  box-shadow: 0 2rpx 10rpx rgba(0, 0, 0, 0.05);
}

.stat-item {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.stat-number {
  font-size: 36rpx;
  font-weight: bold;
  color: #4B7BFF;
  margin-bottom: 10rpx;
}

.stat-label {
  font-size: 26rpx;
  color: #666;
}

/* 功能菜单 */
.menu-list {
  margin: 0 30rpx;
}

.menu-group {
  background-color: #FFFFFF;
  border-radius: 20rpx;
  margin-bottom: 30rpx;
  box-shadow: 0 2rpx 10rpx rgba(0, 0, 0, 0.05);
}

.menu-item {
  display: flex;
  align-items: center;
  padding: 30rpx;
  border-bottom: 1px solid #F5F5F5;
}

.menu-item:last-child {
  border-bottom: none;
}

.menu-icon {
  width: 40rpx;
  height: 40rpx;
  border-radius: 20rpx;
  margin-right: 20rpx;
  background-color: #4B7BFF;
}

.menu-text {
  flex: 1;
  font-size: 28rpx;
  color: #333;
}

.menu-arrow {
  font-size: 28rpx;
  color: #999;
}

/* 菜单图标颜色 */
.competition {
  background-color: #1890FF;
}

.team {
  background-color: #52C41A;
}

.works {
  background-color: #722ED1;
}

.favorite {
  background-color: #F5222D;
}

.history {
  background-color: #FA8C16;
}

.settings {
  background-color: #13C2C2;
}

.feedback {
  background-color: #EB2F96;
}

.about {
  background-color: #722ED1;
}
</style>