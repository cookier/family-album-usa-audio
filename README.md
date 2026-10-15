# 走遍美国 Family Album U.S.A.

经典英语情景教学网站，跟着 Stewart 一家学地道美式英语。

**🔗 在线访问：https://cookier.github.io/family-album-usa-audio/**

## 简介

《走遍美国》（Family Album U.S.A.）是一部经典的英语情景教学节目，以纽约一个四代同堂的美国家庭 Stewart 一家的生活为主线，通过生动的日常对话场景，帮助学习者掌握实用的美式英语。

本项目是一个纯静态的在线学习工具，支持：

- 📖 26集完整剧本，带时间戳同步
- 🎧 音频播放，支持倍速调节（0.5x ~ 2.0x）
- ⏭️ 点击播放自动跳过片头（从第一句台词前 1 秒开始，暂停续播不受影响）
- 🈶 每句英文台词下方常驻中文译文，台词面板可一键隐藏/显示（自动记住）
- 🔍 课程搜索
- ✅ 学习进度追踪（本地存储）
- ⌨️ 键盘快捷键（空格播放/暂停，Esc返回）
- 📱 响应式设计，支持移动端

## 技术栈

**零依赖，零构建，纯原生实现：**

- HTML + CSS + JavaScript（单文件，38KB）
- 数据存储：JSON（episodes.json，约 950KB）
- 音频：MP3 格式
- 进度存储：localStorage
- 部署：任意静态服务器（nginx / Vercel / GitHub Pages）

没有 React、没有 Vue、没有 npm、没有 webpack。打开 `index.html` 就能用。

## 快速开始

```bash
# 克隆仓库
git clone https://github.com/cookier/family-album-usa-audio.git

# 直接打开
open index.html

# 或者用任意 HTTP 服务器
python3 -m http.server 8080
npx serve .
```

## 项目结构

```
family-album-usa/
├── index.html        # 主页面（HTML + CSS + JS 全部内联）
├── episodes.json     # 剧本数据（26集 × 3幕，带时间戳）
├── audio/            # 音频文件（MP3）
│   ├── u0101.mp3     # 第1集第1幕
│   ├── u0102.mp3     # 第1集第2幕
│   └── ...
└── README.md
```

## 数据说明

- **episodes.json**：包含26集完整剧本数据，每行带有时间戳（`t` 字段，单位秒），可与音频同步；每句带中文翻译（`cn` 字段，99.2% 覆盖，译文取自 family-album-usa/data.js 的人工校对版本，经句级文本对齐映射；被音频时间轴拆散的句子已并回源数据的自然句，总行数 6335 → 5602）
- **audio/**：MP3 音频文件，命名规则为 `u{集数:02d}{幕数:02d}.mp3`
- **时间戳校准**：78 幕全部有音频，时间轴来自两条实测链路——
  - ep1-17 的 49 幕：以 LRC 歌词时间轴为基准，按音频互相关实测偏移（+0.10~0.12s）重校；
  - 其余 29 幕（ep1a3、ep12a2、ep18-26）：faster-whisper 转写对齐，并经 LRC 交叉验证、语音起点检测修正了个别错位句。

## 浏览器兼容

- Chrome / Edge 80+
- Firefox 78+
- Safari 14+
- 移动端浏览器

## 许可证

MIT License

## 致谢

- 剧本数据来源：[littleflute/Family-Album-USA](https://github.com/littleflute/Family-Album-USA)
- 音频来源：[Archive.org](https://archive.org)
- 剧本补充：[LovelyLanguage.ru](https://www.lovelylanguage.ru)
- 音频补充：[Bilibili - 走遍美国](https://www.bilibili.com/video/BV1534y1t7AR)

## 免责声明

本项目仅供英语学习用途，音频和剧本版权归原作者所有。请勿用于商业用途。
