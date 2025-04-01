<template>
  <view class="content">
    <view class="header">
      <text class="title">泰语键盘示例</text>
    </view>
    
    <view class="input-section">
      <text class="input-label">请输入泰语文本：</text>
      <view class="input-container" @tap="showKeyboard">
        <text class="input-text">{{ inputText || '点击这里开始输入' }}</text>
      </view>
      
      <view class="preview-section" v-if="inputText">
        <text class="preview-label">输入内容预览：</text>
        <view class="preview-box">
          <text class="preview-text">{{ inputText }}</text>
        </view>
      </view>
      
      <button class="clear-button" @tap="clearInput" v-if="inputText">清空输入</button>
    </view>
    
    <view class="info-section">
      <text class="info-title">关于泰语键盘</text>
      <text class="info-text">泰语是东南亚国家泰国的官方语言，拥有自己独特的文字系统。泰语字母表包含44个辅音字母和15个元音标记，以及4个声调标记。</text>
      <text class="info-text">泰语书写系统是从左到右，从上到下，没有空格来分隔单词，而是使用空格来分隔句子。</text>
      <text class="info-tips">提示：点击上方输入框可以打开泰语键盘。</text>
    </view>
    
    <!-- 泰语键盘组件 -->
    <thai-keyboard 
      :visible="keyboardVisible" 
      @input="onKeyInput" 
      @backspace="onBackspace" 
      @enter="onEnter" 
      @close="hideKeyboard"
    />
  </view>
</template>

<script>
import ThaiKeyboard from '../../components/ThaiKeyboard.vue';

export default {
  components: {
    ThaiKeyboard
  },
  data() {
    return {
      inputText: '',
      keyboardVisible: false
    };
  },
  methods: {
    // 显示键盘
    showKeyboard() {
      this.keyboardVisible = true;
    },
    
    // 隐藏键盘
    hideKeyboard() {
      this.keyboardVisible = false;
    },
    
    // 处理按键输入
    onKeyInput(key) {
      this.inputText += key;
    },
    
    // 处理退格键
    onBackspace() {
      if (this.inputText.length > 0) {
        this.inputText = this.inputText.slice(0, -1);
      }
    },
    
    // 处理确认键
    onEnter() {
      this.hideKeyboard();
      uni.showToast({
        title: '输入完成',
        icon: 'success'
      });
    },
    
    // 清空输入
    clearInput() {
      this.inputText = '';
    }
  }
};
</script>

<style>
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  padding: 20px;
  padding-bottom: 300px; /* 为键盘预留空间 */
}

.header {
  width: 100%;
  text-align: center;
  margin-bottom: 30px;
}

.title {
  font-size: 24px;
  font-weight: bold;
  color: #333;
}

.input-section {
  width: 100%;
  margin-bottom: 30px;
}

.input-label {
  font-size: 16px;
  margin-bottom: 10px;
  display: block;
}

.input-container {
  width: 100%;
  min-height: 100px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 15px;
  box-sizing: border-box;
}

.input-text {
  font-size: 18px;
  color: #333;
  word-break: break-all;
}

.preview-section {
  margin-top: 20px;
}

.preview-label {
  font-size: 16px;
  margin-bottom: 10px;
  display: block;
}

.preview-box {
  background-color: #f9f9f9;
  padding: 15px;
  border-radius: 8px;
  border: 1px solid #eee;
}

.preview-text {
  font-size: 18px;
  color: #333;
  line-height: 1.5;
}

.clear-button {
  margin-top: 15px;
  background-color: #f44336;
  color: white;
}

.info-section {
  width: 100%;
  background-color: #f5f5f5;
  border-radius: 8px;
  padding: 15px;
  margin-top: 20px;
}

.info-title {
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 10px;
  display: block;
}

.info-text {
  font-size: 14px;
  color: #666;
  margin-bottom: 10px;
  display: block;
  line-height: 1.5;
}

.info-tips {
  font-size: 14px;
  color: #007aff;
  margin-top: 10px;
  display: block;
}
</style>