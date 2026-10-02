# BlackHole-GalaxyMerger-Demo · 黑洞与星系合并演示

[English](README.en.md) | 中文

> 单文件、零外部依赖的 WebGL2 实时演示：卡冈图雅式黑洞（逐像素史瓦西测地线光线追踪）、银河系 × 仙女星系合并 / 擦肩模拟（限制性三体）、吸积盘与米勒潮汐行星。用任何现代浏览器打开 `index.html` 即可，无需构建、无需服务器。

**在线演示**: https://ragntec.github.io/BlackHole-GalaxyMerger-Demo/

## 特性

- **逐像素史瓦西零测地线追踪**：黑洞阴影、光子环、引力透镜
- **吸积盘**：自旋相关 ISCO 内缘（Bardeen 公式）、Novikov–Thorne 温度分布、多普勒增亮与引力红移
- **星系合并与交错**：银河系（棒旋）× 仙女星系（旋涡）限制性三体模拟，合并 / 擦肩两种场景，潮汐桥与潮汐尾自然形成
- **米勒潮汐行星**：巨浪、潮汐锁定、时间膨胀读数
- **手机适配**：单指旋转、双指缩放、虚拟摇杆、小屏底部控制抽屉
- **中英双语**：按浏览器语言自动默认简中 / 英文，右上角可手动切换（记住选择）
- **自适应双档渲染**：PC 端 HDR 泛光后期（RGBA16F + 双向高斯泛光 + ACES），手机端单 pass 直出（iPhone WebGL 兼容性设计）
- **录制**：`canvas.captureStream` + `MediaRecorder`，只录制 3D 画面不含 UI

## 本地运行

直接用浏览器打开 `index.html` 即可；推荐起一个本地静态服务：

```bash
python3 -m http.server 8000
# 浏览器访问 http://localhost:8000/
```

需要 WebGL2 支持。桌面端建议使用 Chrome / Edge / Safari 最新版；iPhone 上请用 Safari。

## 代码结构

整个项目就是一个 `index.html`（约 86KB），有意保持单文件、零依赖，方便直接部署到任何静态托管：

| 部分 | 说明 |
| --- | --- |
| GLSL 片元着色器 | 零测地线积分、吸积盘着色、辉光（碰撞参数驱动，单 pass 解析式） |
| JS 物理 | 限制性三体星系模拟、行星 / 相机动力学、自适应分辨率 |
| JS UI | 桌面控制面板、手机手势与底部抽屉、录制、循环演示、中英双语切换 |

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
