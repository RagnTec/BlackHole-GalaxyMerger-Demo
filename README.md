# Gargantua_Demo · 卡冈图雅黑洞演示

> Single-file, zero-dependency WebGL2 demo: a Gargantua-style black hole with per-pixel Schwarzschild geodesic ray tracing, an accretion disk, Miller's tide-locked planet, and a Milky Way × Andromeda merger backdrop. Open `index.html` in any modern browser — no build step, no server required.

单文件、零外部依赖的 WebGL2 实时黑洞演示。灵感来自《星际穿越》中的卡冈图雅（视觉风格参考，非官方复刻）。

**在线演示 / Live demo**：https://ragntec.github.io/Gargantua_Demo/

## 特性

- **逐像素史瓦西零测地线追踪**：黑洞阴影、光子环、引力透镜
- **吸积盘**：ISCO 内缘（6M）、Novikov–Thorne 温度分布、多普勒增亮与引力红移、内缘白热亮环、较差自转亮丝
- **米勒潮汐行星**：巨浪、大气层辉光、时间膨胀读数
- **银河系 × 仙女星系**：棒旋星系 vs 经典旋涡星系（尘埃带、核球、三层核辉光），限制性三体背景模拟，合并 / 擦肩两种场景，支持循环演示
- **手机适配**：单指旋转、双指缩放、虚拟摇杆、小屏底部控制抽屉
- **录制**：`canvas.captureStream` + `MediaRecorder`，只录制 WebGL 画布（不含 UI），悬浮 REC 按钮
- **渲染路径**：单 pass 直出（着色器内 ACES + 伽马 → RGBA8），无多 pass 后期——这是为了 iPhone WebGL 兼容性刻意保留的设计，请勿轻易改为浮点 FBO 管线

## 本地运行

直接用浏览器打开 `index.html` 即可；推荐起一个本地静态服务：

```bash
python3 -m http.server 8000
# 浏览器访问 http://localhost:8000/
```

需要 WebGL2 支持。桌面端建议使用 Chrome / Edge / Safari 最新版；iPhone 上请用 Safari。

## 代码结构

整个项目就是一个 `index.html`（约 64KB），有意保持单文件、零依赖，方便直接部署到任何静态托管：

| 部分 | 说明 |
| --- | --- |
| GLSL 片元着色器 | 零测地线积分、吸积盘着色、辉光（碰撞参数驱动，单 pass 解析式） |
| JS 物理 | 限制性三体星系模拟、行星 / 相机动力学、自适应分辨率 |
| JS UI | 桌面控制面板、手机手势与底部抽屉、录制、循环演示开关 |

`.nojekyll` 用于告诉 GitHub Pages 跳过 Jekyll 构建。

## 贡献指南

欢迎 PR，一起把这个小宇宙做得更好：

1. Fork 本仓库，新建分支（`git checkout -b feat/your-idea`）
2. 保持**单文件、零外部依赖**——这是项目的核心约束，任何引入构建步骤或 CDN 依赖的 PR 都不会被接受
3. 手机端（尤其是 iPhone Safari）是第一优先级：改动后请在真机或至少在移动端模拟器验证无黑屏、无明显掉帧
4. 提交 PR，描述里写清楚改了什么、在什么设备上测过

有想法也可以先开 Issue 讨论（物理准确性、画质、性能都是好话题）。

## License

MIT — 详见 [LICENSE](LICENSE)。
