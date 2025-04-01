<template>
  <view class="thai-keyboard" v-if="visible">
    <view class="keyboard-header">
      <text class="header-title">泰语键盘</text>
      <view class="header-close" @tap="closeKeyboard">关闭</view>
    </view>
    
    <view class="keyboard-content">
      <!-- 辅音字母区域 -->
      <view class="keyboard-section">
        <view class="keyboard-row">
          <view v-for="(key, index) in consonants1" :key="index" class="key" @tap="inputKey(key)">
            <text>{{ key }}</text>
          </view>
        </view>
        <view class="keyboard-row">
          <view v-for="(key, index) in consonants2" :key="index" class="key" @tap="inputKey(key)">
            <text>{{ key }}</text>
          </view>
        </view>
        <view class="keyboard-row">
          <view v-for="(key, index) in consonants3" :key="index" class="key" @tap="inputKey(key)">
            <text>{{ key }}</text>
          </view>
        </view>
      </view>
      
      <!-- 元音区域 -->
      <view class="keyboard-section">
        <view class="keyboard-row">
          <view v-for="(key, index) in vowels" :key="index" class="key" @tap="inputKey(key)">
            <text>{{ key }}</text>
          </view>
        </view>
      </view>
      
      <!-- 声调和特殊字符区域 -->
      <view class="keyboard-section">
        <view class="keyboard-row">
          <view v-for="(key, index) in tones" :key="index" class="key" @tap="inputKey(key)">
            <text>{{ key }}</text>
          </view>
        </view>
      </view>
      
      <!-- 功能按键区域 -->
      <view class="keyboard-section">
        <view class="keyboard-row">
          <view class="key key-space" @tap="inputKey(' ')">
            <text>空格</text>
          </view>
          <view class="key key-backspace" @tap="backspace">
            <text>删除</text>
          </view>
          <view class="key key-enter" @tap="enter">
            <text>确认</text>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  name: 'ThaiKeyboard',
  props: {
    visible: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      // 泰语辅音字母分成三行显示
      consonants1: ['ก', 'ข', 'ฃ', 'ค', 'ฅ', 'ฆ', 'ง', 'จ', 'ฉ', 'ช'],
      consonants2: ['ซ', 'ฌ', 'ญ', 'ฎ', 'ฏ', 'ฐ', 'ฑ', 'ฒ', 'ณ', 'ด'],
      consonants3: ['ต', 'ถ', 'ท', 'ธ', 'น', 'บ', 'ป', 'ผ', 'ฝ', 'พ', 'ฟ', 'ภ', 'ม'],
      
      // 泰语元音
      vowels: ['ะ', 'ั', 'า', 'ำ', 'ิ', 'ี', 'ึ', 'ื', 'ุ', 'ู', 'เ', 'แ', 'โ', 'ใ', 'ไ'],
      
      // 泰语声调标记和其他特殊字符
      tones: ['่', '้', '๊', '๋', '็', '์', 'ๆ', '฿']
    };
  },
  methods: {
    // 输入字符
    inputKey(key) {
      this.$emit('input', key);
    },
    
    // 删除字符
    backspace() {
      this.$emit('backspace');
    },
    
    // 确认输入
    enter() {
      this.$emit('enter');
    },
    
    // 关闭键盘
    closeKeyboard() {
      this.$emit('close');
    }
  }
};
</script>

<style>
.thai-keyboard {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  background-color: #f5f5f5;
  border-top: 1px solid #ddd;
  z-index: 999;
  padding-bottom: env(safe-area-inset-bottom);
}

.keyboard-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 15px;
  border-bottom: 1px solid #ddd;
}

.header-title {
  font-size: 16px;
  font-weight: bold;
}

.header-close {
  color: #007aff;
  font-size: 14px;
}

.keyboard-content {
  padding: 10px;
}

.keyboard-section {
  margin-bottom: 10px;
}

.keyboard-row {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin-bottom: 8px;
}

.key {
  width: 9%;
  height: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #fff;
  border-radius: 5px;
  margin: 0 0.5% 8px;
  box-shadow: 0 1px 3px rgba(0,0,0,0.1);
}

.key-space {
  width: 50%;
}

.key-backspace, .key-enter {
  width: 20%;
}
</style>