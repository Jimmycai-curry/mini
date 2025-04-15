<template>
  <view class="competition-registration-page">
    <!-- 导航栏 -->
    <view class="navigation-bar">
      <view class="status-bar" :style="{ height: statusBarHeight + 'px' }"></view>
      <view class="nav-content">
        <view class="back-icon" @click="navigateBack">
          <image src="/static/icons/icon-back.svg" mode="aspectFit"></image>
        </view>
        <text class="title">作品提交</text>
        <view class="placeholder"></view>
      </view>
    </view>

    <!-- 作品提交表单 -->
    <view class="form-container">
      <!-- 比赛标题 -->
      <view class="competition-title">
        <text class="title">粤港澳大湾区大学生创意节</text>
        <view class="tags">
          <text class="tag">视频</text>
          <view class="tag-line"></view>
          <text class="tag">平面</text>
          <view class="tag-line"></view>
          <text class="tag">策划</text>
          <view class="tag-line"></view>
          <text class="tag">文案</text>
        </view>
      </view>

      <!-- 简介 -->
      <text class="intro">粤港澳大湾区大学生创意节整合政府、学界、业界、品牌四方资源，着力于解决大学生群体缺乏实战平台、品牌难以打入高校场景、业界亚需新鲜血液的多重困境，在各方之间建立起高效互通的桥梁，从品牌真实营销诉求出发，结合高校教学特点真题真做，通过设计类、影视类、文案类。</text>

      <!-- 作者信息表单 -->
      <view class="form-card">
        <view class="form-cell">
          <view class="cell-content">
            <view class="left">
              <text class="input-text">291104</text>
              <text class="sub-text">张三/暨南大学</text>
            </view>
            <view class="right"></view>
          </view>
        </view>
        <view class="add-author-button" @click="addAuthor">
          <image src="/static/icons/vector-add-author.svg" mode="aspectFit" class="icon"></image>
          <text class="button-text">添加多名作者</text>
        </view>
      </view>

      <!-- 指导老师信息 -->
      <view class="form-card">
        <view class="form-cell">
          <view class="cell-content">
            <view class="left">
              <text class="label">指导老师</text>
            </view>
            <view class="right">
              <text class="hint">(选填)</text>
              <image src="/static/icons/arrow-right.svg" mode="aspectFit" class="arrow-icon"></image>
            </view>
          </view>
        </view>
      </view>

      <!-- 提示文字 -->
      <text class="hint-text">*作者/指导老师将以此页面最终保存结果自上而下的顺序为准。</text>

      <!-- 作品信息表单 -->
      <view class="form-card">
        <!-- 作品名称 -->
        <view class="form-cell">
          <view class="cell-content">
            <view class="left">
              <text class="hint-input">请输入作品名称</text>
            </view>
            <view class="right"></view>
          </view>
          <view class="card-line"></view>
        </view>

        <!-- 命题选择 -->
        <view class="form-cell">
          <view class="cell-content">
            <view class="left">
              <text class="label">命题选择</text>
            </view>
            <view class="right">
              <image src="/static/icons/arrow-right.svg" mode="aspectFit" class="arrow-icon"></image>
            </view>
          </view>
          <view class="card-line"></view>
        </view>

        <!-- 作品类别 -->
        <view class="form-cell">
          <view class="cell-content">
            <view class="left">
              <text class="label">作品类别</text>
            </view>
            <view class="right">
              <image src="/static/icons/arrow-right.svg" mode="aspectFit" class="arrow-icon"></image>
            </view>
          </view>
          <view class="card-line"></view>
        </view>

        <!-- 创意思想 -->
        <view class="form-cell">
          <view class="textarea-content">
            <text class="label">创意思想</text>
            <textarea class="input-textarea" 
                      placeholder="请输入作品创意" 
                      placeholder-class="placeholder-style" 
                      maxlength="200" 
                      v-model="creativeIdea"
                      @input="countWords"></textarea>
            <text class="word-count">{{creativeIdeaLength}}/200</text>
          </view>
          <view class="card-line textarea-line"></view>
        </view>

        <!-- AI工具使用 -->
        <view class="form-cell">
          <view class="cell-content">
            <view class="left">
              <text class="label">本作品是否使用人工智能工具</text>
            </view>
            <view class="right">
              <image src="/static/icons/arrow-right.svg" mode="aspectFit" class="arrow-icon"></image>
            </view>
          </view>
          <view class="card-line"></view>
        </view>

        <!-- 作品提交 -->
        <view class="form-cell">
          <view class="upload-content">
            <text class="label">作品提交</text>
            <text class="upload-hint">支持JPG/JPGE/PDF/MOV，单个文件不大于20M。</text>
          </view>
          <view class="upload-button" @click="uploadWork">
            <image src="/static/icons/vector-upload-file.svg" mode="aspectFit" class="icon"></image>
            <text class="button-text">上传作品</text>
          </view>
        </view>
      </view>

      <!-- 条例同意 -->
      <view class="agreement">
        <view class="checkbox" @click="toggleAgreement">
          <image v-if="isAgreed" src="/static/icons/checkbox-checked.svg" mode="aspectFit" class="checkbox-icon"></image>
          <view v-else class="checkbox-unchecked"></view>
        </view>
        <text class="agreement-text">本小组全体成员已阅读并同意《相关条例》</text>
      </view>

      <!-- 底部提交按钮 -->
      <view class="bottom-area">
        <button class="submit-button" :disabled="!isAgreed" @click="submitForm">提交作品</button>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';

// 状态栏高度
const statusBarHeight = ref(20);

// 创意思想文本内容及长度
const creativeIdea = ref('');
const creativeIdeaLength = ref(0);

// 是否同意条款
const isAgreed = ref(false);

// 获取状态栏高度
onMounted(() => {
  // 获取系统信息
  uni.getSystemInfo({
    success: (res) => {
      statusBarHeight.value = res.statusBarHeight || 20;
    }
  });
});

// 返回上一页
const navigateBack = () => {
  uni.navigateBack();
};

// 添加作者
const addAuthor = () => {
  console.log('添加作者');
  // 这里可以添加弹窗或者跳转到添加作者页面的逻辑
};

// 上传作品
const uploadWork = () => {
  uni.chooseFile({
    count: 1,
    type: 'all',
    success: (res) => {
      console.log('选择文件成功', res);
      // 处理文件上传
    },
    fail: (err) => {
      console.error('选择文件失败', err);
    }
  });
};

// 计算字数
const countWords = () => {
  creativeIdeaLength.value = creativeIdea.value.length;
};

// 切换同意条款状态
const toggleAgreement = () => {
  isAgreed.value = !isAgreed.value;
};

// 提交表单
const submitForm = () => {
  if (!isAgreed.value) {
    uni.showToast({
      title: '请先同意相关条例',
      icon: 'none'
    });
    return;
  }
  
  console.log('提交表单');
  // 这里添加表单提交逻辑
};
</script>

<style lang="scss" scoped>
.competition-registration-page {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  background-color: #F5F5FA;
}

/* 导航栏样式 */
.navigation-bar {
  background: #5258F2; /* 主题色 */
  color: #FFFFFF;
  
  .nav-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 44px;
    padding: 0 16px;
    
    .back-icon {
      width: 24px;
      height: 24px;
      display: flex;
      align-items: center;
      justify-content: center;
      
      image {
        width: 18px;
        height: 18px;
      }
    }
    
    .title {
      font-size: 17px;
      font-weight: 400;
      flex: 1;
      text-align: center;
    }
    
    .placeholder {
      width: 24px;
    }
  }
}

/* 表单容器 */
.form-container {
  display: flex;
  flex-direction: column;
  padding: 20px 20px 40px;
  gap: 12px;
}

/* 比赛标题 */
.competition-title {
  display: flex;
  flex-direction: column;
  gap: 4px;
  
  .title {
    font-size: 17px;
    font-weight: 500;
    color: #191658;
    line-height: 1.4em;
  }
  
  .tags {
    display: flex;
    align-items: center;
    gap: 6px;
    
    .tag {
      font-size: 12px;
      color: #696693;
      line-height: 1.4em;
    }
    
    .tag-line {
      width: 1px;
      height: 10px;
      background-color: #D8D8F1;
    }
  }
}

/* 简介 */
.intro {
  font-size: 14px;
  color: #666666;
  line-height: 1.4em;
}

/* 表单卡片 */
.form-card {
  background-color: #FFFFFF;
  border-radius: 8px;
  border: 0.5px solid #C6C7FD;
  display: flex;
  flex-direction: column;
  padding: 4px 1px;
  
  &:first-of-type {
    padding: 4px 1px 20px;
  }
}

/* 表单单元格 */
.form-cell {
  padding: 16px 12px;
  position: relative;
}

/* 单元格内容 */
.cell-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  
  .left {
    display: flex;
    flex-direction: column;
    gap: 4px;
    
    .input-text, .label {
      font-size: 15px;
      line-height: 1.6em;
      color: #333333;
    }
    
    .sub-text {
      font-size: 15px;
      line-height: 1.6em;
      color: #999999;
    }
    
    .hint-input {
      font-size: 15px;
      line-height: 1.6em;
      color: #999999;
    }
  }
  
  .right {
    display: flex;
    align-items: center;
    gap: 4px;
    
    .hint {
      font-size: 15px;
      line-height: 1.6em;
      color: #999999;
    }
    
    .arrow-icon {
      width: 16px;
      height: 16px;
    }
  }
}

/* 分隔线 */
.card-line {
  position: absolute;
  height: 0.5px;
  background-color: #D8D8F1;
  left: 12px;
  right: 12px;
  bottom: 0;
}

/* 添加作者按钮 */
.add-author-button {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 2px;
  padding: 8px 12px;
  margin: 0 12px;
  border: 1px solid #7071EA;
  border-radius: 8px;
  
  .icon {
    width: 16px;
    height: 16px;
  }
  
  .button-text {
    font-size: 14px;
    color: #7071EA;
    line-height: 1.4em;
  }
}

/* 提示文本 */
.hint-text {
  font-size: 10px;
  color: #666666;
  line-height: 1.4em;
}

/* 文本域内容 */
.textarea-content {
  display: flex;
  flex-direction: column;
  gap: 8px;
  position: relative;
  
  .label {
    font-size: 15px;
    line-height: 1.6em;
    color: #333333;
  }
  
  .input-textarea {
    font-size: 15px;
    line-height: 1.6em;
    min-height: 100px;
    width: 100%;
    box-sizing: border-box;
  }
  
  .placeholder-style {
    color: #999999;
  }
  
  .word-count {
    position: absolute;
    right: 0;
    bottom: -20px;
    font-size: 10px;
    color: #999999;
  }
}

.textarea-line {
  bottom: -24px;
}

/* 上传内容 */
.upload-content {
  display: flex;
  flex-direction: column;
  gap: 4px;
  
  .label {
    font-size: 15px;
    line-height: 1.6em;
    color: #333333;
  }
  
  .upload-hint {
    font-size: 10px;
    color: #666666;
    line-height: 1.4em;
  }
}

/* 上传按钮 */
.upload-button {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 2px;
  padding: 8px 12px;
  margin-top: 12px;
  border: 1px solid #7071EA;
  border-radius: 8px;
  
  .icon {
    width: 16px;
    height: 16px;
  }
  
  .button-text {
    font-size: 14px;
    color: #7071EA;
    line-height: 1.4em;
  }
}

/* 协议同意 */
.agreement {
  display: flex;
  align-items: center;
  gap: 4px;
  margin-top: 8px;
  
  .checkbox {
    width: 18px;
    height: 18px;
    display: flex;
    align-items: center;
    justify-content: center;
    
    .checkbox-icon {
      width: 18px;
      height: 18px;
    }
    
    .checkbox-unchecked {
      width: 16px;
      height: 16px;
      border: 0.8px solid #7071EA;
      border-radius: 50%;
    }
  }
  
  .agreement-text {
    font-size: 14px;
    color: #333333;
    line-height: 1.78em;
  }
}

/* 底部区域 */
.bottom-area {
  display: flex;
  justify-content: center;
  margin-top: 16px;
  
  .submit-button {
    width: 100%;
    background-color: #5258F2;
    color: #FFFFFF;
    font-size: 15px;
    font-weight: 500;
    padding: 8px 16px;
    border-radius: 18px;
    line-height: 1.4em;
    
    &:disabled {
      opacity: 0.5;
    }
  }
}
</style> 