<template>
  <view class="container">
    <!-- 自定义导航栏 -->
    <view class="custom-nav">
      <view class="nav-title">
        <text class="title-text">消息中心</text>
        <text class="title-en">MESSAGES</text>
      </view>
      <view class="nav-right">
        <image class="nav-icon" src="/static/icons/notification.svg" mode="aspectFit"></image>
      </view>
    </view>
    
    <!-- 消息分类 -->
    <view class="message-tabs">
      <view class="tab active">全部</view>
      <view class="tab">系统</view>
      <view class="tab">比赛</view>
      <view class="tab">队伍</view>
    </view>
    
    <!-- 消息列表 -->
    <view class="message-list">
      <!-- 系统消息 -->
      <view class="message-item system">
        <view class="message-icon system-icon">
          <text class="icon-text">系统</text>
        </view>
        <view class="message-content">
          <view class="message-title">系统通知</view>
          <view class="message-text">欢迎使用灵感学院小程序，这里有最新的创意比赛信息！</view>
          <view class="message-time">2023-10-25 10:30</view>
        </view>
      </view>
      
      <!-- 比赛消息 -->
      <view class="message-item competition">
        <view class="message-icon competition-icon">
          <text class="icon-text">比赛</text>
        </view>
        <view class="message-content">
          <view class="message-title">粤港澳大湾区大学生创意节</view>
          <view class="message-text">您关注的比赛将于12天后截止提交，请抓紧时间完成作品！</view>
          <view class="message-time">2023-10-24 15:45</view>
        </view>
      </view>
      
      <!-- 队伍消息 -->
      <view class="message-item team">
        <view class="message-icon team-icon">
          <text class="icon-text">队伍</text>
        </view>
        <view class="message-content">
          <view class="message-title">创意无限队</view>
          <view class="message-text">张三邀请您加入"创意无限队"参加粤港澳大湾区大学生创意节</view>
          <view class="message-time">2023-10-23 09:15</view>
          <view class="message-actions">
            <view class="action-btn accept">接受</view>
            <view class="action-btn decline">拒绝</view>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

onMounted(() => {
  console.log('消息页面加载完成')
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

/* 消息分类标签 */
.message-tabs {
  display: flex;
  background-color: #FFFFFF;
  padding: 20rpx 30rpx;
  margin-bottom: 20rpx;
}

.tab {
  padding: 10rpx 30rpx;
  font-size: 28rpx;
  color: #666;
  margin-right: 20rpx;
  border-radius: 30rpx;
}

.tab.active {
  background-color: #4B7BFF;
  color: #FFFFFF;
}

/* 消息列表 */
.message-list {
  padding: 0 30rpx;
}

.message-item {
  display: flex;
  background-color: #FFFFFF;
  border-radius: 20rpx;
  padding: 30rpx;
  margin-bottom: 20rpx;
  box-shadow: 0 2rpx 10rpx rgba(0, 0, 0, 0.05);
}

.message-icon {
  width: 80rpx;
  height: 80rpx;
  border-radius: 40rpx;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-right: 20rpx;
  flex-shrink: 0;
}

.system-icon {
  background-color: #FFC53D;
}

.competition-icon {
  background-color: #1890FF;
}

.team-icon {
  background-color: #52C41A;
}

.icon-text {
  color: #FFFFFF;
  font-size: 24rpx;
}

.message-content {
  flex: 1;
}

.message-title {
  font-size: 30rpx;
  font-weight: bold;
  color: #333;
  margin-bottom: 10rpx;
}

.message-text {
  font-size: 26rpx;
  color: #666;
  margin-bottom: 10rpx;
  line-height: 1.5;
}

.message-time {
  font-size: 24rpx;
  color: #999;
  margin-bottom: 10rpx;
}

.message-actions {
  display: flex;
  margin-top: 10rpx;
}

.action-btn {
  padding: 6rpx 20rpx;
  border-radius: 30rpx;
  font-size: 24rpx;
  margin-right: 20rpx;
}

.accept {
  background-color: #4B7BFF;
  color: #FFFFFF;
}

.decline {
  background-color: #F5F5F5;
  color: #666;
}
</style>