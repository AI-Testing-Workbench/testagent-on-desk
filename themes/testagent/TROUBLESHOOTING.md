# Kiro Face 主题 - 故障排除

## 问题：切换主题后角色消失

### 症状
- 右键菜单选择 "Kiro Face" 主题后
- 桌面上的 Clawd 角色完全消失
- 只能看到空白或透明区域

### 原因
这个问题已在 v1.0.1 中修复。如果你仍然遇到此问题：

### 解决方案

#### 1. 确认使用最新版本
```bash
# 查看主题版本
cat themes/kiro/theme.json | grep version
# 应该显示 "1.0.0" 或更高

# 如果版本较旧，重新拉取代码
git pull origin main
```

#### 2. 清除主题缓存
```bash
# macOS
rm -rf ~/Library/Application\ Support/clawd-on-desk/theme-cache/kiro

# Linux
rm -rf ~/.config/clawd-on-desk/theme-cache/kiro

# Windows
rmdir /s "%APPDATA%\clawd-on-desk\theme-cache\kiro"
```

#### 3. 重启 Clawd
```bash
# 完全退出 Clawd（右键托盘图标 → Quit）
# 然后重新启动
npm start
```

#### 4. 验证主题文件
```bash
node scripts/validate-theme.js themes/kiro
# 应该显示 "All checks passed!"
```

#### 5. 测试 SVG 文件
在浏览器中打开测试页面：
```bash
open themes/kiro/test-single.html
```
如果能看到蓝色圆脸，说明 SVG 文件正常。

---

## 问题：眼睛追踪不工作

### 症状
- 角色显示正常
- 但眼睛不跟随鼠标移动

### 解决方案

#### 1. 检查配置
确认 `theme.json` 中：
```json
{
  "eyeTracking": {
    "enabled": true,
    "states": ["idle"]
  }
}
```

#### 2. 检查 SVG 结构
打开 `assets/idle-follow.svg`，确认包含：
```svg
<g id="eyes-js">
  <!-- 眼睛元素 -->
</g>
```

#### 3. 确认在空闲状态
眼睛追踪只在 `idle` 状态下工作。如果 Clawd 正在工作或思考，眼睛不会追踪。

---

## 问题：动画不流畅

### 症状
- 角色显示正常
- 但动画卡顿或不流畅

### 解决方案

#### 1. 检查 GPU 加速
确保浏览器/Electron 启用了硬件加速。

#### 2. 减小窗口尺寸
右键 Clawd → Size → 选择 Small 或 Medium

#### 3. 关闭其他占用 GPU 的应用
- 视频播放器
- 游戏
- 其他 Electron 应用

---

## 问题：点击无反应

### 症状
- 无法拖动 Clawd
- 右键菜单不出现
- 点击没有反应

### 解决方案

#### 1. 检查 hitBox 配置
确认 `theme.json` 中：
```json
{
  "hitBoxes": {
    "default": { "x": -1, "y": 5, "w": 17, "h": 12 }
  }
}
```

#### 2. 尝试点击角色中心
点击圆脸的中心位置，而不是边缘。

#### 3. 重启应用
有时需要重启 Clawd 才能应用新的 hitBox 设置。

---

## 问题：某些状态显示异常

### 症状
- 大部分状态正常
- 但某个特定状态（如 building）显示异常

### 解决方案

#### 1. 检查 SVG 文件
```bash
# 在浏览器中单独打开该 SVG
open themes/kiro/assets/building.svg
```

#### 2. 检查 viewBox
确保所有 SVG 使用相同的 viewBox：
```svg
<svg viewBox="-15 -25 45 45" ...>
```

#### 3. 检查动画语法
确认 CSS `@keyframes` 语法正确，没有拼写错误。

---

## 问题：主题没出现在菜单中

### 症状
- 右键 Clawd → Theme
- 菜单中没有 "Kiro Face" 选项

### 解决方案

#### 1. 检查目录结构
```bash
themes/kiro/
├── theme.json
└── assets/
    ├── idle-follow.svg
    └── ...
```

#### 2. 检查 JSON 语法
```bash
# 验证 JSON 格式
cat themes/kiro/theme.json | python -m json.tool
```

#### 3. 检查文件权限
```bash
chmod -R 755 themes/kiro
```

#### 4. 重启 Clawd
主题列表在启动时加载，需要重启才能看到新主题。

---

## 问题：颜色显示不正确

### 症状
- 角色显示但颜色不对
- 渐变边框不显示

### 解决方案

#### 1. 检查渐变定义
确认每个 SVG 都包含：
```svg
<defs>
  <linearGradient id="borderGrad" ...>
    <stop offset="0%" stop-color="#4fc3f7"/>
    <stop offset="50%" stop-color="#2979ff"/>
    <stop offset="100%" stop-color="#69f0ae"/>
  </linearGradient>
</defs>
```

#### 2. 检查 ID 冲突
确保每个 SVG 的渐变 ID 唯一（或在同一文件内）。

---

## 仍然有问题？

### 调试步骤

1. **查看控制台日志**
   ```bash
   # 启动时添加调试标志
   npm start
   # 查看终端输出的错误信息
   ```

2. **使用默认主题对比**
   ```bash
   # 切换回默认 Clawd 主题
   # 如果默认主题正常，说明是 Kiro 主题的问题
   ```

3. **检查文件完整性**
   ```bash
   # 确认所有 18 个 SVG 文件都存在
   ls -la themes/kiro/assets/*.svg | wc -l
   # 应该显示 18
   ```

4. **重新验证主题**
   ```bash
   node scripts/validate-theme.js themes/kiro
   ```

### 报告问题

如果以上方法都无法解决，请提供以下信息：

- 操作系统和版本
- Clawd 版本
- 主题版本（`theme.json` 中的 version 字段）
- 错误信息（如果有）
- 复现步骤

---

## 常见误区

❌ **错误**: 修改 SVG 后没有清除缓存
✅ **正确**: 修改后删除 `theme-cache/kiro` 并重启

❌ **错误**: 使用不同的 viewBox 尺寸
✅ **正确**: 所有 SVG 使用统一的 `viewBox="-15 -25 45 45"`

❌ **错误**: 忘记在 `idle-follow.svg` 中添加 `id="eyes-js"`
✅ **正确**: 眼睛追踪需要特定的 SVG 结构

❌ **错误**: 修改 `theme.json` 后没有重启
✅ **正确**: 配置更改需要重启 Clawd 才能生效

---

## 快速检查清单

- [ ] 主题版本 >= 1.0.1
- [ ] 所有 18 个 SVG 文件存在
- [ ] `theme.json` 语法正确
- [ ] viewBox 设置为 `-15 -25 45 45`
- [ ] hitBoxes 配置正确
- [ ] objectScale 使用默认值
- [ ] 清除了主题缓存
- [ ] 重启了 Clawd
- [ ] 验证脚本通过

如果所有项都打勾，主题应该能正常工作！
