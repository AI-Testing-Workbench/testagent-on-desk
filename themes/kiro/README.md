# Kiro Face Theme

一个基于 Kiro 头像设计的可爱蓝色圆脸主题，具有渐变边框和丰富的表情动画。

## 特点

- 🎨 蓝色渐变边框（青色 → 蓝色 → 绿色）
- 👀 眼睛追踪鼠标移动
- 😊 12 种表情状态
- ✨ 流畅的 CSS 动画
- 💙 简约可爱的设计风格

## 状态映射

| 状态 | 动画效果 |
|------|---------|
| 空闲 (idle) | 眼睛跟随鼠标，自动眨眼 |
| 思考 (thinking) | 眼睛左右移动，光环脉冲 |
| 工作 (typing) | 快速眨眼，轻微弹跳 |
| 构建 (building) | 戴魔术师帽，帽子摇摆 |
| 杂耍 (juggling) | 眼睛上下移动 |
| 开心 (happy) | 弯弧笑眼，弹跳庆祝 |
| 通知 (notification) | 惊讶大眼，脉冲放大 |
| 错误 (error) | 难过眼睛，流泪摇晃 |
| 打哈欠 (yawning) | 半闭眼，身体拉伸 |
| 睡眠 (sleeping) | 闭眼横线，Z Z Z 飘起 |
| 醒来 (waking) | 眼睛睁开，身体摇晃 |
| 清扫 (sweeping) | 左右摇摆 |
| 搬运 (carrying) | 上下移动 |

## 反应动画

- **拖拽**: 惊讶表情 + 左右摇摆
- **左击**: 左眼眨眼 + 向左倾斜
- **右击**: 右眼眨眼 + 向右倾斜
- **双击**: 旋转 + 爱心飘起

## 安装方法

### 方法 1：从源码运行

如果你是从项目源码运行 Clawd：

```bash
# 主题已经在 themes/kiro/ 目录中
# 启动 Clawd
npm start

# 右键点击 Clawd → Theme → 选择 "Kiro Face"
```

### 方法 2：安装到用户目录

如果你使用的是已安装的 Clawd 应用：

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

然后重启 Clawd，右键菜单中选择 "Kiro Face" 主题。

## 技术细节

- **格式**: 纯 SVG + CSS 动画
- **画布尺寸**: 28x28 单位 (viewBox: -2 -2 28 28)
- **眼睛追踪**: 支持（最大偏移 2px）
- **迷你模式**: 暂不支持
- **文件大小**: 每个 SVG 约 1-2KB

## 自定义

你可以轻松修改主题颜色：

1. 编辑 `assets/*.svg` 文件
2. 修改渐变色：
   - `#4fc3f7` (青色)
   - `#2979ff` (蓝色)
   - `#69f0ae` (绿色)
3. 修改眼睛颜色：`#2979ff`
4. 修改背景色：`#e8f4ff`

## 许可证

MIT License

基于 Kiro 头像设计创作。
