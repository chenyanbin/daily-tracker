# 日常打卡 (Daily Tracker)

## 项目概述
纯前端 H5 单页应用，用于记录每日事项并标记完成状态。

## 技术栈
- 原生 HTML + CSS + JavaScript（无框架）
- 数据存储：localStorage
- 无构建工具，直接在浏览器中打开即可运行

## 文件结构
- `index.html` — 单文件应用（HTML + 内联 CSS + 内联 JS）
- `manifest.webmanifest` — PWA 应用清单
- `sw.js` — Service Worker（离线缓存）
- `icon.svg` — 应用图标

## 核心功能
1. 添加/删除每日事项
2. 勾选标记完成（checkbox）
3. 日期切换（前一天/后一天/回到今天）
4. 键盘快捷键：← → 切换日期，T 回到今天
5. 统计：总计、已完成、完成率、进度条
6. 预设模板快速添加（早起、读书、运动等）
7. 数据导入/导出（JSON 格式）
8. 清空当天记录

## 数据格式
localStorage key: `daily-tracker-data`
```json
{
  "2026-06-05": [
    { "id": "xxx", "name": "早起", "done": false, "createdAt": 1234567890 }
  ]
}
```

## 编码规范
- 注释用中文（面向中文用户）
- 函数命名用 camelCase
- CSS 变量定义在 `:root` 中
- 新增功能保持零依赖，不引入第三方库
- 保持移动端优先的响应式设计（max-width: 480px）

## 注意事项
- 这是一个纯静态应用，不要引入 Node.js、npm、构建工具等
- 数据只存在浏览器 localStorage 中，无后端、无数据库
- 修改文件后直接在浏览器打开 index.html 测试即可
- 导入数据时会合并（覆盖同名日期的数据），不是替换
- UI 界面是中文的，新增文案也用中文
- Service Worker 仅在 http(s) 下生效，本地 file:// 协议会跳过注册

## 部署 / 在微信中打开
1. **本地预览**：直接双击 `index.html`（Service Worker 不会激活，但应用可用）
2. **本地局域网测试**：`python3 -m http.server 8080`，手机访问 `http://<电脑IP>:8080`
3. **发布到公网**（推荐）：
   - 拖拽整个文件夹到 Cloudflare Pages / Vercel / Netlify
   - 或推送到 GitHub 仓库，开启 GitHub Pages
4. **微信使用**：把公网链接发到"文件传输助手" → 点开链接 → 右上角"…" → "在浏览器打开" → 浏览器菜单"添加到主屏幕"，即可像 App 一样使用
