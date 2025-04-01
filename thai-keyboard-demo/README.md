# 泰语键盘 UniApp 示例

这是一个使用UniApp框架开发的泰语键盘示例项目，展示了如何在跨平台应用中实现泰语输入功能。

## 项目结构

```
thai-keyboard-demo/
├── components/
│   └── ThaiKeyboard.vue      # 泰语键盘组件
├── pages/
│   └── index/
│       └── index.vue         # 主页面
├── static/                   # 静态资源目录
├── App.vue                   # 应用主组件
├── main.js                   # 应用入口文件
├── manifest.json             # 应用配置
├── pages.json                # 页面路由配置
└── uni.scss                  # 全局样式变量
```

## 功能特点

- 完整的泰语字符键盘布局，包括：
  - 44个辅音字母
  - 15个元音标记
  - 4个声调标记和特殊字符
- 响应式布局，适配不同设备尺寸
- 基本的键盘功能（输入、删除、确认、空格）
- 简洁直观的用户界面

## 如何使用

1. 在HBuilderX中导入项目
2. 运行到模拟器或真机进行测试
3. 点击输入框即可打开泰语键盘
4. 使用键盘输入泰语文本

## 如何在自己的项目中使用

1. 复制 `components/ThaiKeyboard.vue` 到您的项目中
2. 在需要的页面引入并注册组件：

```javascript
import ThaiKeyboard from '@/components/ThaiKeyboard.vue';

export default {
  components: {
    ThaiKeyboard
  }
}
```

3. 在模板中使用组件：

```html
<thai-keyboard 
  :visible="keyboardVisible" 
  @input="onKeyInput" 
  @backspace="onBackspace" 
  @enter="onEnter" 
  @close="hideKeyboard"
/>
```

## 自定义键盘布局

您可以通过修改 `ThaiKeyboard.vue` 文件中的数据来自定义键盘布局：

```javascript
data() {
  return {
    consonants1: ['ก', 'ข', 'ฃ', 'ค', ...],
    consonants2: ['ซ', 'ฌ', 'ญ', 'ฎ', ...],
    consonants3: ['ต', 'ถ', 'ท', 'ธ', ...],
    vowels: ['ะ', 'ั', 'า', 'ำ', ...],
    tones: ['่', '้', '๊', '๋', ...]
  };
}
```

## 许可

MIT