<script>
export default {
  onLaunch: function() {
    console.log('App Launch');
  },
  onShow: function() {
    console.log('App Show');
  },
  onHide: function() {
    console.log('App Hide');
  }
};
</script>

<style>
/* 全局样式 */
page {
  background-color: #f8f8f8;
  font-family: -apple-system, BlinkMacSystemFont, 'Helvetica Neue', Helvetica,
    Segoe UI, Arial, Roboto, 'PingFang SC', 'miui', 'Hiragino Sans GB', 'Microsoft Yahei',
    sans-serif;
}

/* 泰文字体支持 */
.thai-font {
  font-family: 'Noto Sans Thai', 'Tahoma', sans-serif;
}

/* 统一按钮样式 */
button {
  margin: 10px 0;
}

/* 去除按钮默认边框 */
button::after {
  border: none;
}
</style>