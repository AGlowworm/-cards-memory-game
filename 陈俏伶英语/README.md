## 🛠️ 配置说明

### 基础环境要求
| 组件       | 最低要求                  |
|------------|--------------------------|
| 浏览器     | Chrome 90+ / Firefox 85+ |
| 分辨率     | 1280x720 及以上          |
| 网络       | 本地或在线访问           |

##❓常见问题

安装类问题

Q1: 打开页面后只显示空白
✅ 解决方案：

检查浏览器控制台错误（F12 > Console）

确认 images/ 文件夹存在且包含以下文件：

images/
├── react.png
├── angular.png
├── vue.png
...（共 8 个图标文件）
在 index.html 中验证资源路径：


<!-- 正确示例 -->
<img src="images/react.png" alt="React Logo">

Q2: 重置按钮点击无反应
✅ 排查步骤：

确保浏览器未禁用弹出窗口

检查 reset 按钮的事件监听：


// 在 js/script.js 中应存在
resetButton.addEventListener('click', initGame);
运行类问题

Q3: 卡片翻转动画卡顿
🔧 优化建议：

启用浏览器硬件加速：

/* 在 css/style.css 添加 */
.card {
  transform: translateZ(0);
}
降低动画复杂度（修改 transition 时间）

Q4: 移动设备点击延迟严重
📱 临时解决方案：
添加触摸事件支持到 js/script.js：

card.addEventListener('touchstart', function(e) {
  e.preventDefault();
  handleCardClick(e);
});

逻辑类问题

Q5: 已匹配的卡片仍可点击
⚙️ 技术说明：
匹配成功的卡片应添加 matched 类并移除事件监听：

// 正确逻辑应包含
card.classList.add('matched');
card.removeEventListener('click', handleCardClick);

Q6: 计时器在后台标签页加速
⏳ 已知问题：
由于浏览器节能策略，可使用 Web Worker 改进计时精度，示例代码见 docs/timer-fix.md

