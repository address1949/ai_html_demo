# ai_html_demo

一个零依赖的 HTML 演示项目：用纯 **SVG + SMIL** 手绘了一只**骑自行车的鹈鹕**动画。

## 运行

直接用浏览器打开即可，无需构建、无需网络、无任何外部依赖：

```bash
# 方式一：直接打开
open index.html            # macOS
xdg-open index.html        # Linux

# 方式二：起个本地服务
python3 -m http.server 8000
# 浏览器访问 http://localhost:8000
```

## 动画构成

全部动画由 SVG 原生 SMIL（`<animate>` / `<animateTransform>`）驱动，共 17 条时间线：

| 元素 | 技术 | 周期 |
| --- | --- | --- |
| 前后车轮辐条 | `animateTransform type="rotate"` | 0.5s |
| 曲柄与脚踏 | 绕中轴 `(366,320)` 旋转 | 0.9s |
| 双腿踩踏板 | `<animate attributeName="d">` 形变关键帧 | 0.9s |
| 翅膀扇动 / 前伸搭车把 | rotate 关键帧 | 0.6s |
| 围巾被风吹 | `d` 形变 | 0.8s |
| 车身颠簸 | 整体 translate | 0.6s |
| 路面虚线后移 | `stroke-dashoffset` | 0.35s |
| 草丛 / 云朵后掠 | translate | 0.9s / 26–34s |
| 太阳光芒旋转、眨眼 | rotate / opacity | 24s / 3.4s |

## 文件

```
ai_html_demo/
├── index.html   # 页面 + 内联 SVG 场景（天空、远山、草地、路面）
└── README.md
```

## 说明

- 场景 `viewBox="0 0 800 450"`，响应式自适应宽度。
- SMIL 在 Chrome / Edge / Safari / Firefox 均可用；不依赖 JavaScript。
