# Kiro Face 主题 - 快速开始

## 🎯 一分钟上手

### 1. 预览主题

在浏览器中打开 `test-preview.html` 查看所有动画效果：

```bash
# macOS/Linux
open themes/kiro/test-preview.html

# Windows
start themes/kiro/test-preview.html
```

### 2. 应用主题

#### 方式 A：从源码运行（推荐）

```bash
# 1. 启动 Clawd
npm start

# 2. 右键点击桌面上的 Clawd
# 3. 选择 Theme → Kiro Face
```

#### 方式 B：安装到用户目录

**macOS:**
```bash
cp -r themes/kiro ~/Library/Application\ Support/clawd-on-desk/themes/
```

**Linux:**
```bash
cp -r themes/kiro ~/.config/clawd-on-desk/themes/
```

**Windows:**
```cmd
xcopy /E themes\kiro "%APPDATA%\clawd-on-desk\themes\kiro\"
```

然后重启 Clawd，在主题菜单中选择 "Kiro Face"。

### 3. 验证主题

```bash
node scripts/validate-theme.js themes/kiro
```

应该看到 "All checks passed!" 消息。

## 📊 主题信息

| 项目 | 详情 |
|------|------|
| 名称 | Kiro Face |
| 版本 | 1.0.0 |
| 文件数 | 18 个 SVG + 1 个配置 |
| 总大小 | ~22 KB |
| 格式 | 纯 SVG + CSS 动画 |
| 眼睛追踪 | ✅ 支持 |
| 迷你模式 | ❌ 暂不支持 |

## 🎨 状态一览

### 核心状态（8 个）
- ✅ idle - 空闲（眼睛追踪）
- ✅ thinking - 思考（光环脉冲）
- ✅ working/typing - 工作（快速眨眼）
- ✅ happy - 开心（弹跳庆祝）
- ✅ notification - 通知（惊讶大眼）
- ✅ error - 错误（流泪摇晃）
- ✅ sleeping - 睡眠（Z Z Z）
- ✅ waking - 醒来（眼睛睁开）

### 工作层级（3 个）
- ✅ typing - 1 个会话
- ✅ juggling - 2 个会话
- ✅ building - 3+ 个会话（魔术帽）

### 额外状态（4 个）
- ✅ yawning - 打哈欠
- ✅ sweeping - 清扫
- ✅ carrying - 搬运
- ✅ idle-look - 随机空闲动画

### 反应动画（4 个）
- ✅ react-drag - 拖拽
- ✅ react-left - 左击
- ✅ react-right - 右击
- ✅ react-double - 双击

## 🎭 表情对照

| 表情 | 眼睛形状 | 特殊效果 |
|------|---------|---------|
| 默认 | 竖椭圆 | 眨眼 |
| 开心 | 弯弧 ^_^ | 弹跳 |
| 惊讶 | 大圆 | 高光 |
| 思考 | 左右移动 | 光环 |
| 害羞 | 小圆点 | 腮红 |
| 困惑 | 一大一小 | - |
| 得意 | 横线 -_- | - |
| 哭泣 | 倒弧 | 泪滴 |

## 🔧 自定义颜色

编辑任意 SVG 文件中的渐变定义：

```svg
<linearGradient id="borderGrad" x1="0%" y1="0%" x2="100%" y2="100%">
  <stop offset="0%" stop-color="#4fc3f7"/>   <!-- 青色 -->
  <stop offset="50%" stop-color="#2979ff"/>  <!-- 蓝色 -->
  <stop offset="100%" stop-color="#69f0ae"/> <!-- 绿色 -->
</linearGradient>
```

### 推荐配色方案

**紫色系：**
```svg
<stop offset="0%" stop-color="#ba68c8"/>
<stop offset="50%" stop-color="#9c27b0"/>
<stop offset="100%" stop-color="#e1bee7"/>
```

**橙色系：**
```svg
<stop offset="0%" stop-color="#ffb74d"/>
<stop offset="50%" stop-color="#ff9800"/>
<stop offset="100%" stop-color="#ffe0b2"/>
```

**绿色系：**
```svg
<stop offset="0%" stop-color="#81c784"/>
<stop offset="50%" stop-color="#4caf50"/>
<stop offset="100%" stop-color="#c8e6c9"/>
```

## 🐛 故障排除

### 主题没出现在菜单中
- 检查 `theme.json` 是否是有效的 JSON
- 确认文件路径正确
- 重启 Clawd 应用

### 眼睛追踪不工作
- 确认 `idle-follow.svg` 包含 `id="eyes-js"`
- 检查 `theme.json` 中 `eyeTracking.enabled` 为 `true`

### 动画不流畅
- 检查 GPU 加速是否启用
- 尝试减小窗口尺寸
- 关闭其他占用 GPU 的应用

### SVG 显示异常
- 运行验证脚本：`node scripts/validate-theme.js themes/kiro`
- 检查 SVG 文件是否损坏
- 确认 viewBox 设置正确

## 📚 更多资源

- **完整文档**: `README.md`
- **详细预览**: `PREVIEW.md`
- **主题创建指南**: `../../docs/guide-theme-creation.md`
- **在线预览**: `test-preview.html`

## 💡 提示

1. **最佳尺寸**: 推荐使用中等尺寸（120px），在右键菜单中调整
2. **性能优化**: 纯 CSS 动画，无 JavaScript 开销
3. **任意缩放**: SVG 矢量图形，放大不失真
4. **自定义**: 所有 SVG 文件都可以用文本编辑器修改

## 🎉 享受你的主题！

如果你喜欢这个主题，可以：
- ⭐ 给项目点个 Star
- 🐛 报告问题或建议
- 🎨 创建你自己的主题变体
- 💬 分享给其他开发者

---

Made with 💙 for Clawd on Desk
