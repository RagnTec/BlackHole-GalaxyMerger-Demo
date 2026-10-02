# BlackHole-GalaxyMerger-Demo · 黑洞与星系合并演示

> Single-file, zero-dependency WebGL2 demo: a Gargantua-style black hole rendered with per-pixel Schwarzschild geodesic ray tracing, a Milky Way × Andromeda merger/flyby simulation (restricted three-body), an accretion disk, and Miller's tide-locked planet. Open `index.html` in any modern browser — no build step, no server required.

> 单文件、零外部依赖的 WebGL2 实时演示：卡冈图雅式黑洞（逐像素史瓦西测地线光线追踪）、银河系 × 仙女星系合并 / 擦肩模拟（限制性三体）、吸积盘与米勒潮汐行星。用任何现代浏览器打开 `index.html` 即可，无需构建、无需服务器。

**在线演示 / Live demo**: https://ragntec.github.io/GargantuaDemo/

## 特性 / Features

- **逐像素史瓦西零测地线追踪 / Per-pixel Schwarzschild ray tracing**：黑洞阴影、光子环、引力透镜 / black-hole shadow, photon ring, gravitational lensing
- **吸积盘 / Accretion disk**：自旋相关 ISCO 内缘（Bardeen 公式）、Novikov–Thorne 温度分布、多普勒增亮与引力红移 / spin-dependent ISCO inner edge (Bardeen), Novikov–Thorne temperature profile, Doppler beaming and gravitational redshift
- **星系合并与交错 / Galaxy merger & flyby**：银河系（棒旋）× 仙女星系（旋涡）限制性三体模拟，合并 / 擦肩两种场景，潮汐桥与潮汐尾自然形成 / Milky Way (barred spiral) × Andromeda (spiral) restricted three-body simulation with merger and flyby scenarios; tidal bridges and tails emerge naturally
- **米勒潮汐行星 / Miller's planet**：巨浪、潮汐锁定、时间膨胀读数 / giant waves, tidal locking, time-dilation readout
- **手机适配 / Mobile ready**：单指旋转、双指缩放、虚拟摇杆、小屏底部控制抽屉 / one-finger rotate, pinch zoom, virtual joystick, bottom control drawer on small screens
- **中英双语 / Bilingual UI**：按浏览器语言自动默认简中 / 英文，右上角可手动切换（记住选择）/ auto-detects browser language, manual toggle at top-right (choice is remembered)
- **自适应双档渲染 / Adaptive rendering**：PC 端 HDR 泛光后期（RGBA16F + 双向高斯泛光 + ACES），手机端单 pass 直出（iPhone WebGL 兼容性设计）/ HDR bloom pipeline on desktop (RGBA16F + separable Gaussian bloom + ACES), single-pass direct output on mobile (designed around iPhone WebGL constraints)
- **录制 / Recording**：`canvas.captureStream` + `MediaRecorder`，只录制 3D 画面不含 UI / records only the 3D canvas, not the UI

## 本地运行 / Run Locally

直接用浏览器打开 `index.html` 即可；推荐起一个本地静态服务：

```bash
python3 -m http.server 8000
# 浏览器访问 http://localhost:8000/
```

需要 WebGL2 支持。桌面端建议使用 Chrome / Edge / Safari 最新版；iPhone 上请用 Safari。

---

Just open `index.html` in a browser; or serve it locally:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/
```

Requires WebGL2. Latest Chrome / Edge / Safari recommended on desktop; use Safari on iPhone.

## 代码结构 / Code Structure

整个项目就是一个 `index.html`（约 86KB），有意保持单文件、零依赖，方便直接部署到任何静态托管：

The whole project is a single `index.html` (~86KB) — intentionally dependency-free, so it can be deployed to any static hosting as-is:

| 部分 / Part | 说明 / Description |
| --- | --- |
| GLSL 片元着色器 / Fragment shader | 零测地线积分、吸积盘着色、辉光（碰撞参数驱动，单 pass 解析式）/ geodesic integration, disk shading, analytic glow |
| JS 物理 / Physics | 限制性三体星系模拟、行星 / 相机动力学、自适应分辨率 / restricted three-body galaxy sim, planet/camera dynamics, adaptive resolution |
| JS UI | 桌面控制面板、手机手势与底部抽屉、录制、循环演示、中英双语切换 / desktop panel, mobile gestures & drawer, recording, demo looping, bilingual toggle |

`.nojekyll` 用于告诉 GitHub Pages 跳过 Jekyll 构建 / tells GitHub Pages to skip Jekyll processing.

## 贡献指南 / Contributing

欢迎 PR，一起把这个小宇宙做得更好：

1. Fork 本仓库，新建分支（`git checkout -b feat/your-idea`）
2. 保持**单文件、零外部依赖**——这是项目的核心约束，任何引入构建步骤或 CDN 依赖的 PR 都不会被接受
3. 手机端（尤其是 iPhone Safari）是第一优先级：改动后请在真机或至少在移动端模拟器验证无黑屏、无明显掉帧
4. 提交 PR，描述里写清楚改了什么、在什么设备上测过

---

PRs are welcome — let's make this little universe better together:

1. Fork the repo and create a branch (`git checkout -b feat/your-idea`)
2. Keep it **single-file, zero-dependency** — this is the project's core constraint; any PR introducing build steps or CDN dependencies will not be accepted
3. Mobile (especially iPhone Safari) is the top priority: please verify on a real device or at least a mobile emulator that there is no black screen and no major frame drops
4. Open the PR describing what changed and which devices you tested on

有想法也可以先开 Issue 讨论（物理准确性、画质、性能都是好话题）/ Feel free to open an Issue first to discuss ideas (physics accuracy, visuals, and performance are all great topics).

## License

MIT — 详见 / see [LICENSE](LICENSE)。
