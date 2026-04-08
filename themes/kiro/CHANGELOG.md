# Kiro Face Theme - 更新日志

## v1.0.1 - 2024-04-07

### 🐛 修复
- **修复角色消失问题**: 调整 viewBox 从 `28x28` 到 `45x45` 以匹配 Clawd 默认渲染尺寸
- **修复点击区域**: 更新 hitBoxes 坐标以正确响应鼠标交互
- **修复缩放比例**: 调整 objectScale 参数使角色正确显示
- **修复眼睛追踪**: 更新 shadowOrigin 和相关参数以正确追踪鼠标

### 🎨 改进
- 重新绘制所有 18 个 SVG 文件以适配新的 viewBox
- 优化眼睛位置和大小比例
- 调整动画的 transform-origin 以确保流畅效果
- 统一所有状态的视觉风格

### 📐 技术细节

**之前的配置（有问题）:**
```json
{
  "viewBox": { "x": -2, "y": -2, "width": 28, "height": 28 },
  "hitBoxes": {
    "default": { "x": 0, "y": 0, "w": 24, "h": 24 }
  },
  "objectScale": {
    "widthRatio": 2.0,
    "heightRatio": 2.0,
    "offsetX": 0,
    "offsetY": 0
  }
}
```

**修复后的配置:**
```json
{
  "viewBox": { "x": -15, "y": -25, "width": 45, "height": 45 },
  "hitBoxes": {
    "default": { "x": -1, "y": 5, "w": 17, "h": 12 }
  },
  "objectScale": {
    "widthRatio": 1.9,
    "heightRatio": 1.3,
    "offsetX": -0.45,
    "offsetY": -0.25
  }
}
```

### ✅ 验证
- 通过 `validate-theme.js` 所有检查
- 在浏览器中测试所有动画正常
- 眼睛追踪功能正常工作

---

## v1.0.0 - 2024-04-07

### 🎉 初始版本
- 创建基于 Kiro 头像设计的主题
- 18 个动画状态（12 个核心 + 4 个反应 + 2 个额外）
- 蓝色渐变边框设计
- 眼睛追踪鼠标功能
- 纯 SVG + CSS 动画实现
