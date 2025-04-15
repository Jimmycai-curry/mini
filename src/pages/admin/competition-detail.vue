<template>
  <view class="competition-detail-page">
    <!-- 1. Navigation -->
    <view class="navigation-bar">
      <view class="back-icon" @click="navigateBack">‹</view> <!-- 使用简单的字符代替返回图标 -->
      <text class="title">赛事详情</text>
      <view class="placeholder"></view> <!-- 用于占位使标题居中 -->
    </view>

    <!-- 2. Video Placeholder -->
    <view class="video-placeholder">
      <image src="/static/images/video.png" mode="aspectFill" class="video-image"></image>
      <!-- 可以添加播放按钮图标 -->
    </view>

    <!-- 3. Title Section -->
    <view class="title-section">
      <view class="main-title-area">
          <text class="main-title">2022粤港澳大湾区大学生创意节</text>
          <view class="tags">
              <text class="tag">视频</text>
              <text class="tag-separator">|</text>
              <text class="tag">平面</text>
              <text class="tag-separator">|</text>
              <text class="tag">策划</text>
              <text class="tag-separator">|</text>
              <text class="tag">文案</text>
          </view>
      </view>
      <view class="bookmark-area">
          <view class="bookmark-icon">☆</view> <!-- 使用简单的字符代替收藏图标 -->
          <text class="bookmark-count">3279</text>
      </view>
    </view>

    <!-- 4. Tab Bar -->
    <view class="tab-bar">
       <text
         v-for="tab in tabs"
         :key="tab.id"
         :class="['tab-item', { active: activeTab === tab.id }]"
         @click="changeTab(tab.id)"
       >
         {{ tab.name }}
       </text>
    </view>

    <!-- Tab Content -->
    <view v-show="activeTab === 'overview'" class="tab-content">
      <!-- 5. 比赛概况 -->
      <view class="section">
        <text class="section-title">简介</text>
        <text class="section-content">{{ competitionDetails.intro }}</text>
      </view>
      <view class="section">
        <text class="section-title">指导单位</text>
        <text class="section-content">{{ competitionDetails.guidanceUnits }}</text>
      </view>
       <view class="section">
        <text class="section-title">赛事命题</text>
        <text class="section-content">点击下方企业logo查看命题与下载相关资料。</text>
        <!-- 此处未来可添加企业logo图片按钮 -->
        <view class="company-logos">
            <!-- 示例Logo占位 -->
            <view class="logo-placeholder">企业A</view>
            <view class="logo-placeholder">企业B</view>
            <view class="logo-placeholder">企业C</view>
            <view class="logo-placeholder">企业D</view>
        </view>
      </view>
      <view class="section">
        <text class="section-title">参赛资格</text>
        <text class="section-content">{{ competitionDetails.eligibility }}</text>
      </view>
      <view class="section">
        <text class="section-title">参赛规定</text>
        <text class="section-content">{{ competitionDetails.rules }}</text>
      </view>
      <view class="section">
        <text class="section-title">作品创作时间</text>
        <text class="section-content">{{ competitionDetails.creationTime }}</text>
      </view>
      <view class="section">
        <text class="section-title">参赛作品类别</text>
        <text class="section-content">{{ competitionDetails.categories }}</text>
      </view>
      <view class="section">
        <text class="section-title">作品标准</text>
        <text class="section-content">{{ competitionDetails.standards }}</text>
      </view>

      <!-- 6. 最新活动 -->
       <view class="section latest-activities">
           <text class="section-title">最新活动</text>
           <view class="activity-list">
               <view v-for="(activity, index) in relatedActivities" :key="index" class="activity-card">
                   <image :src="activity.image" mode="aspectFill" class="activity-image"></image>
                   <view class="activity-info">
                       <text class="activity-title">{{ activity.title }}</text>
                       <text class="activity-time">{{ activity.time }}</text>
                       <text class="activity-location">{{ activity.participants }}人 | {{ activity.method }} | {{ activity.location }}</text>
                   </view>
                   <view :class="['activity-status', activity.status === 'recruiting' ? 'recruiting' : 'starting']">
                       {{ activity.status === 'recruiting' ? '招募中' : '即将开始' }}
                   </view>
                   <view class="bookmark-icon-activity">☆</view> <!-- 活动卡片上的收藏图标 -->
               </view>
           </view>
       </view>
    </view>

    <view v-show="activeTab === 'topics'" class="tab-content">
      <!-- 赛事命题内容将在这里添加 -->
      <text>赛事命题内容 - 待填充</text>
    </view>
    <view v-show="activeTab === 'rules'" class="tab-content">
      <!-- 参赛细则内容将在这里添加 -->
      <text>参赛细则内容 - 待填充</text>
    </view>
    <view v-show="activeTab === 'faq'" class="tab-content">
      <!-- 常见问题内容将在这里添加 -->
      <text>常见问题内容 - 待填充</text>
    </view>

     <!-- 7. Bottom Bar -->
    <view class="bottom-bar">
        <view class="deadline-info">
            <text class="deadline-date">{{ deadline.date }} 24:00</text>
            <text class="deadline-remaining">截止剩余{{ deadline.remaining }}</text>
        </view>
        <button class="share-button" open-type="share">分享</button>
        <button class="participate-button" @click="navigateToRegistration">参与赛事</button>
    </view>

  </view>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';
import { onLoad } from '@dcloudio/uni-app';

// Tab Bar State
const tabs = ref([
  { id: 'overview', name: '比赛概况' },
  { id: 'topics', name: '赛事命题' },
  { id: 'rules', name: '参赛细则' },
  { id: 'faq', name: '常见问题' },
]);
const activeTab = ref('overview'); // 默认选中比赛概况

const changeTab = (tabId: string) => {
  activeTab.value = tabId;
};

// Navigation
const navigateBack = () => {
  uni.navigateBack();
};

// 5. Competition Details Data
const competitionDetails = ref({
  intro: '粤港澳大湾区大学生创意节整合政府、学界、业界、品牌四方资源，着力于解决大学生群体缺乏实战平台、品牌难以打入高校场景、业界亚需新鲜血液的多重困境，在各方之间建立起高效互通的桥梁，从品牌真实营销诉求出发，结合高校教学特点真题真做，通过设计类、影视类、文案类。',
  guidanceUnits: '广东海外联谊会\n中央人民政府驻香港特别行政区联络办公室广东联络部\n中央人民政府驻澳门特别行政区联络办公室教育与青年工作部\n广州海外联谊会\n海珠海外联谊会',
  eligibility: '2022粤港澳大湾区大学生创意节参赛对象为全国（含港澳台）专科、高职、本科、硕士、博士等各类院校在读学生。同时接受中国境内就读的外国留学生和赴国外留学的中国留学生及全球在校大学生参赛。',
  rules: '参赛作品必须按照本届粤港澳大湾区大学生创意节组委会统一指定的命题策略单和规定的品牌主背景资料进行创作。命题策略单及品牌主素材文件详见粤港澳湾创节官方网站：www.gbaccf.com',
  creationTime: '2023年3月31日24:00截止报名',
  categories: '具体参赛作品类别以命题策略单要求为准。\n（一）设计类：平面设计、包装设计、产品设计、插画等\n（二）影像类：短视频、短片、微电影等\n（三）策划类：一页提案/H5提案\n（四）文案类：短文案、长文案、广告口号、创意脚本等',
  standards: '1.报名：① 参赛者报名时应如实填写各项内容，不得虚报、瞒报信息，由虚报、瞒报引发的一切后果由参赛人自行承担。 \n② 递交作品通过粤港澳大湾区大学生创意节官网（可通过粤港澳大湾区大学生创意节官方公众号获取官网报名链接）按照要求引导进行报名。\n③ 禁止一稿多投，指同一件作品按不同类别提交或创意雷同作品按不同命题提交，也不能将别的赛事创作的作品再投粤港澳湾创节，一经发现，取消参赛资格。 \n④ 参赛作品任何部分严禁出现参赛学生的姓名及其他特殊标记。\n2.原创：① 支持原创，杜绝抄袭。作品不允许大量或全部使用素材（如平面素材，影视类混剪等），素材须取得官方或作者本人授权才可使用。\n② 本届粤港澳大湾区大学生创意节的参赛选手须保证所提交作品的原创性，如参赛作品涉嫌抄袭、剽窃等非原创的情况，经举报查实，组委会有权取消该件作品的参赛资格。如获奖，则取消该件作品的获奖资格，并在官方媒体进行公示。\n3.版权：① 所有参赛作品所有权将归主办方所有，同意参加比赛则代表同意此参赛须知。为便于作品上传至竞赛系统，赛事期间暂不收集作品源文件，参赛选手需在参赛后一年内保留作品源文件以便后期可能的作品采纳和落地需求。\n② 如因参赛选手提交的参赛作品违反法律法规的规定或侵犯第三方的合法权益的，导致本届粤港澳大湾区大学生创意节官方及品牌方因发布和展览参赛选手的参赛作品而引起任何争议、索赔、诉讼或其他任何纠纷，由此产生的全部责任由参赛选手承担。\n③ 对本参赛须知及著作权承诺等产生疑义，本届粤港澳大湾区大学生创意节组委会将保留最终解释权'
});

// 6. Related Activities Data
const relatedActivities = ref([
  {
    image: '/static/images/activity1.png', // 假设的图片路径
    title: '创意集训营丨粤港澳湾创节',
    time: '2024.4.10-2024.4.15',
    location: '广州天河区珠江新城',
    method: '腾讯会议',
    participants: 50,
    status: 'recruiting' // recruiting or starting
  },
  {
    image: '/static/images/activity2.png', // 假设的图片路径
    title: '创意集训营丨粤港澳湾创节',
    time: '2024.4.10-2024.4.15',
    location: '广州天河区珠江新城',
    method: '腾讯会议',
    participants: 50,
    status: 'starting'
  }
]);

// 7. Bottom Bar Data & Logic
const deadline = ref({
    date: '2025.12.22',
    remaining: '' // 将在 onLoad 中计算
});

const calculateRemainingTime = (deadlineDate: string) => {
    const now = new Date();
    // 将 "yyyy.MM.dd" 转换为 iOS 兼容的 "yyyy-MM-dd" 格式，并修改24:00:00为23:59:59
    const formattedDate = deadlineDate.replace(/\./g, '-') + ' 23:59:59';
    const end = new Date(formattedDate);
    const diff = end.getTime() - now.getTime();

    if (diff <= 0) {
        return '已截止';
    }

    const days = Math.floor(diff / (1000 * 60 * 60 * 24));
    const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
    return `${days}天${hours}小时`;
};

const navigateToRegistration = () => {
    // 跳转到赛事报名页面，需要替换为实际路径
    uni.navigateTo({ url: '/pages/admin/competition-registration' });
    console.log('跳转到赛事报名页');
}

// 页面逻辑将在这里添加
onLoad((options) => {
  if (options?.id) {
    const competitionId = options.id;
    console.log('接收到的赛事ID:', competitionId);
    // 在这里根据 competitionId 加载对应的赛事详情数据
    // fetchCompetitionData(competitionId);
  }
  // 计算剩余时间
  deadline.value.remaining = calculateRemainingTime(deadline.value.date);
})

// 添加分享逻辑（可选）
// onShareAppMessage(() => {
//   return {
//     title: '邀请你参加2022粤港澳大湾区大学生创意节',
//     path: '/pages/admin/competition-detail?id=YOUR_COMPETITION_ID' // 分享路径
//   };
// })

</script>

<style scoped lang="scss">
// 导入或定义主题色变量
// :root {
//   --theme-theme: rgba(82, 88, 242, 1);
// }

.competition-detail-page {
  display: flex;
  flex-direction: column;
  background-color: #f8f8f8; // 页面背景色
}

/* 1. 导航栏样式 */
.navigation-bar {
  display: flex; // 使用弹性布局，让子元素横向排列
  align-items: center; // 子元素在垂直方向上居中对齐
  justify-content: space-between; // 子元素在水平方向上两端对齐，使标题居中
  height: 120rpx; // 设置导航栏高度为120rpx
  padding: 0 30rpx; // 设置左右内边距为30rpx
  padding-top: var(--status-bar-height); // 顶部内边距为状态栏高度，用于适配不同手机型号
  background: var(--theme-theme, rgba(82, 88, 242, 1)); // 设置导航栏背景色，使用主题色变量，默认值为蓝色
  color: white; // 设置文字颜色为白色

  .back-icon {
    font-size: 60rpx; // 设置返回图标字体大小
    width: 100rpx; // 设置返回图标区域宽度
    cursor: pointer; // 鼠标悬停时显示手型光标
  }
  .title {
    font-size: 32rpx; // 设置标题文字大小
    font-weight: bold; // 设置标题文字加粗
  }
   .placeholder {
     width: 60rpx; // 设置占位元素宽度，与返回图标宽度一致，用于保持标题居中
   }
}

/* 2. Video Placeholder */
.video-placeholder {
  width: 100%;
  height: 400rpx; // 示例高度
  background-color: #000;
  position: relative;
  .video-image {
    width: 100%;
    height: 100%;
  }
  // 可以添加播放按钮样式
}

/* 3. Title Section */
.title-section {
  display: flex;
  justify-content: space-between;
  align-items: flex-start; // 垂直顶部对齐
  padding: 30rpx;
  background-color: #fff;
  margin-bottom: 20rpx;

  .main-title-area {
      flex: 1;
      margin-right: 20rpx;
      .main-title {
          font-size: 36rpx;
          font-weight: bold;
          color: #333;
          display: block;
          margin-bottom: 15rpx;
      }
      .tags {
         display: flex;
         align-items: center;
         flex-wrap: wrap;
         color: #666;
         font-size: 24rpx;
         .tag-separator {
             margin: 0 8rpx;
         }
      }
  }

  .bookmark-area {
      display: flex;
      flex-direction: column;
      align-items: center;
      color: #666;
      .bookmark-icon {
          font-size: 40rpx; // 调整图标大小
          color: #ff9900; // 示例颜色
          margin-bottom: 5rpx;
      }
      .bookmark-count {
          font-size: 24rpx;
      }
  }
}

/* 4. Tab Bar */
.tab-bar {
  display: flex;
  justify-content: space-around;
  background-color: #fff;
  padding: 20rpx 0;
  border-bottom: 1rpx solid #eee;
  margin-bottom: 20rpx;

  .tab-item {
    font-size: 28rpx;
    color: #666;
    padding: 10rpx 20rpx;
    position: relative;
    cursor: pointer;

    &.active {
      color: var(--theme-theme, rgba(82, 88, 242, 1));
      font-weight: bold;
      &::after {
        content: '';
        position: absolute;
        bottom: -10rpx;
        left: 50%;
        transform: translateX(-50%);
        width: 60%;
        height: 6rpx;
        background-color: var(--theme-theme, rgba(82, 88, 242, 1));
        border-radius: 3rpx;
      }
    }
  }
}

/* Tab Content Area */
.tab-content {
  background-color: #fff;
  padding: 30rpx;
  margin-bottom: 140rpx; // 增加底部栏空间
}

/* Section Styling */
.section {
  margin-bottom: 40rpx;
  .section-title {
    font-size: 30rpx;
    font-weight: bold;
    color: #333;
    margin-bottom: 15rpx;
    display: block;
  }
  .section-content {
    font-size: 26rpx;
    color: #555;
    line-height: 1.6;
    white-space: pre-wrap; // 保留换行符
  }
}

/* Company Logos Placeholder */
.company-logos {
    display: flex;
    flex-wrap: wrap;
    gap: 20rpx;
    margin-top: 20rpx;
    .logo-placeholder {
        padding: 10rpx 20rpx;
        border: 1rpx solid #eee;
        border-radius: 8rpx;
        font-size: 24rpx;
        color: #666;
        // 替换为实际图片样式
    }
}

/* Latest Activities Styling */
.latest-activities {
    .section-title {
         margin-bottom: 20rpx;
    }
}
.activity-list {
  display: flex;
  flex-direction: column;
  gap: 20rpx; // 活动卡片之间的间距
}

.activity-card {
  display: flex;
  background-color: #fff;
  border-radius: 16rpx;
  padding: 20rpx;
  box-shadow: 0 4rpx 12rpx rgba(0, 0, 0, 0.05);
  position: relative;

  .activity-image {
    width: 200rpx;
    height: 140rpx;
    border-radius: 8rpx;
    margin-right: 20rpx;
    flex-shrink: 0; // 防止图片被压缩
  }

  .activity-info {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    font-size: 24rpx;
    color: #666;
    .activity-title {
      font-size: 28rpx;
      font-weight: bold;
      color: #333;
      margin-bottom: 8rpx;
      // 最多显示两行
      overflow: hidden;
      text-overflow: ellipsis;
      display: -webkit-box;
      -webkit-line-clamp: 2;
      -webkit-box-orient: vertical;
    }
    .activity-time {
        margin-bottom: 4rpx;
    }
     .activity-location {
        font-size: 22rpx;
        color: #999;
    }
  }

  .activity-status {
    position: absolute;
    top: 20rpx;
    right: 20rpx;
    padding: 6rpx 12rpx;
    border-radius: 6rpx;
    font-size: 22rpx;
    font-weight: bold;
    &.recruiting {
      background-color: rgba(82, 88, 242, 0.1);
      color: var(--theme-theme, rgba(82, 88, 242, 1));
    }
    &.starting {
      background-color: rgba(255, 153, 0, 0.1);
      color: #ff9900;
    }
  }

  .bookmark-icon-activity {
      position: absolute;
      bottom: 20rpx;
      right: 20rpx;
      font-size: 36rpx;
      color: #ccc; // 未收藏状态
      // 可以添加点击切换收藏状态的逻辑和样式
  }
}


/* 7. Bottom Bar Styling */
.bottom-bar {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20rpx 30rpx;
    background-color: #fff;
    border-top: 1rpx solid #eee;
    box-shadow: 0 -2rpx 10rpx rgba(0,0,0,0.05);
    padding-bottom: constant(safe-area-inset-bottom); // 适配 iPhone X 等底部安全区域
    padding-bottom: env(safe-area-inset-bottom);

    .deadline-info {
        display: flex;
        flex-direction: column;
        font-size: 22rpx;
        color: #999;
        .deadline-date {
            font-size: 26rpx;
            color: #333;
            margin-bottom: 4rpx;
        }
    }

    button {
        margin-left: 20rpx;
        padding: 0 40rpx;
        height: 70rpx;
        line-height: 70rpx;
        font-size: 28rpx;
        border-radius: 35rpx;
    }

    .share-button {
        background-color: #fff;
        color: var(--theme-theme, rgba(82, 88, 242, 1));
        border: 1rpx solid var(--theme-theme, rgba(82, 88, 242, 1));
    }

    .participate-button {
        background: var(--theme-theme, rgba(82, 88, 242, 1));
        color: #fff;
    }

     // 微信小程序button边框处理
    button::after {
        border: none;
    }
}


</style> 