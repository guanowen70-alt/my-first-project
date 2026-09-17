# 电商 AI 生图 / 视频 开源项目清单

> 本清单根据一份调研 PDF 整理，列出其中提到的、可用于电商「AI 生图（商品图 / 模特试衣）」与「视频生成（带货视频 / 动态试衣）」的开源项目。
>
> 下列 **7 个项目均已 Fork 到本账号 `guanowen70-alt`**，可在 GitHub 主页直接看到；点击「我的 fork」即可进入你自己的副本。
>
> 数据更新时间：2026-09-17（Stars / 最近更新 由 GitHub API 抓取）。

---

## 总览（按 Star 排序，方便筛选）

| # | 项目 | 分类 | Stars | 最近更新 | 我的 fork |
|---|------|------|------:|----------|-----------|
| 1 | ecom-details-image | 生图·详情图 | 1169 | 2026-05-15 | [链接](https://github.com/guanowen70-alt/ecom-details-image) |
| 2 | clipforge（带货剪手） | 短视频 | 825 | 2026-09-16 | [链接](https://github.com/guanowen70-alt/clipforge) |
| 3 | opentryon / OpenTryOn | 虚拟试衣 | 535 | 2026-09-14 | [链接](https://github.com/guanowen70-alt/opentryon) |
| 4 | Fashion-AI | 生图·爆款流水线 | 322 | 2026-05-06 | [链接](https://github.com/guanowen70-alt/Fashion-AI) |
| 5 | tryon-examples | 试衣视频流 | 36 | 2026-05-25 | [链接](https://github.com/guanowen70-alt/tryon-examples) |
| 6 | ai-tryon / TryOn AI | 虚拟试衣 SaaS | 14 | 2026-09-02 | [链接](https://github.com/guanowen70-alt/ai-tryon) |
| 7 | 302_ecom_image_generator | 生图·场景图 | 15 | 2025-08-25 | [链接](https://github.com/guanowen70-alt/302_ecom_image_generator) |

---

## 一、电商 AI 生图、爆款主图与模特生成

### 1. Fashion-AI（电商生图爆款流水线）
- **我的 fork**：https://github.com/guanowen70-alt/Fashion-AI
- **原始仓库**：https://github.com/liangdabiao/Fashion-AI ｜ ⭐ Stars：322 ｜ 最近更新：2026-05-06
- **用途**：全自动 AI 生图流水线。输入新品平铺图，自动在历史爆款库做混合检索（以图搜图 + 销量过滤），找到风格最接近的爆款；随后用 LLM 分析爆款的场景 / 灯光 / 姿势并生成 Prompt，控制 AI 输出专业电商宣传图和模特图。适合跨境电商批量铺货。
- **技术栈**：混合检索、大模型 Prompt 分析、Stable Diffusion。

### 2. 302_ecom_image_generator（电商场景图生成器）
- **我的 fork**：https://github.com/guanowen70-alt/302_ecom_image_generator
- **原始仓库**：https://github.com/302ai/302_ecom_image_generator ｜ ⭐ Stars：15 ｜ 最近更新：2025-08-25
- **用途**：专注商品背景替换与重新打光。根据提供的产品图 / 平铺模特图 + 场景描述，在保持产品本身不变形的前提下重新打光、融合，生成色彩一致的高清场景图，同时支持直接生成场景图视频。
- **特点**：提供开箱即用的前端 Web 界面，适合本地自部署修改。

### 3. ecom-details-image（电商详情图生成器）
- **我的 fork**：https://github.com/guanowen70-alt/ecom-details-image
- **原始仓库**：https://github.com/liangdabiao/ecom-details-image ｜ ⭐ Stars：1169 ｜ 最近更新：2026-05-15
- **用途**：面向电商视觉创作与详情页排版的项目。内置创新的 Campaign Style Lock（品牌风格锁定）机制，输入产品图后，可一键批量输出纯色底主图、场景化生活图、详情页插图、社媒推广图等全套视觉素材。

---

## 二、电商虚拟试衣（Virtual Try-On）与模特替换

### 1. opentryon / OpenTryOn（虚拟试衣工具箱）
- **我的 fork**：https://github.com/guanowen70-alt/opentryon
- **原始仓库**：https://github.com/tryonlabs/opentryon ｜ ⭐ Stars：535 ｜ 最近更新：2026-09-14
- **用途**：TryOnLabs 开源的时尚电商 AI 工具箱。提供用于构建虚拟试衣和时尚拍摄（Photoshoots）的开源 API、SDK 和基础模型，允许开发者深度定制服装的材质、褶皱以及模特的动作。

### 2. ai-tryon / TryOn AI（生产级虚拟试衣 SaaS）
- **我的 fork**：https://github.com/guanowen70-alt/ai-tryon
- **原始仓库**：https://github.com/SamurAIGPT/ai-tryon ｜ ⭐ Stars：14 ｜ 最近更新：2026-09-02
- **用途**：开源 AI 虚拟试衣工具，定位为「production-ready Next.js SaaS」。PDF 中描述的「ai-tryon / TryOn AI 生产级虚拟试衣 SaaS（Next.js + PostgreSQL + Google OAuth + Stripe 积分扣费）」与该仓库高度吻合，已基本确认为同一项目，故补充 Fork。
- **说明**：若你发现实际仓库并非 PDF 所指，可在 GitHub 删除该 fork，并告诉我正确仓库名。

---

## 三、电商短视频、带货视频自动生成

### 1. ClipForge（原名：带货剪手）
- **我的 fork**：https://github.com/guanowen70-alt/clipforge
- **原始仓库**：https://github.com/xixihhhh/clipforge ｜ ⭐ Stars：825 ｜ 最近更新：2026-09-16
- **用途**：专为电商打造的 AI 带货短视频神器。商家只需上传一张商品图，AI 就会自动提炼卖点、撰写种草脚本、配音、加字幕，并锁定商品图原图不变形，一键产出符合抖音 / 快手 / 小红书 / TikTok 规格的卖货短视频。支持 0 成本批量出片、开源无水印、本地自部署。
- **技术栈**：ASR / TTS 音频流、LLM 脚本生成、自动化视频剪辑渲染。

### 2. tryon-examples（实时 WebRTC 试衣视频流）
- **我的 fork**：https://github.com/guanowen70-alt/tryon-examples
- **原始仓库**：https://github.com/DecartAI/tryon-examples ｜ ⭐ Stars：36 ｜ 最近更新：2026-05-25
- **用途**：由 DecartAI 开源的实时视频虚拟试衣方案。允许消费者在网页端直接打开摄像头（Webcam），通过 WebRTC 技术将衣服 reference 图无缝渲染在实时运动的视频人体上，实现无服务器端延迟的「动态魔镜试衣」。

---

## 部署建议

若具备一定技术基础，除以上独立项目外，强烈建议搜索并部署 **ComfyUI** 相关生态插件（如 `ComfyUI-IC-Light` 用于产品重新打光、`LayerDiffusion` 用于透明图层生成）。各大工作流分享社区中有大量现成的「电商换背景」「平铺图穿在真人模特身上」的 `.json` 工作流，直接导入即可高精度生产。

> 注：以上 Stars 与「最近更新」为 2026-09-17 通过 GitHub API 抓取的快照，后续可能变化；如需刷新，重新拉取各仓库数据即可。
