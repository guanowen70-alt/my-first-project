# 电商 AI 生图 / 视频 开源项目清单

> 本清单根据一份调研 PDF 整理，列出其中提到的、可用于电商「AI 生图（商品图 / 模特试衣）」与「视频生成（带货视频 / 动态试衣）」的开源项目。
>
> 下列 **6 个项目已 Fork 到本账号 `guanowen70-alt`**，可在 GitHub 主页直接看到；点击「我的 fork」即可进入你自己的副本。

---

## 一、电商 AI 生图、爆款主图与模特生成

### 1. Fashion-AI（电商生图爆款流水线）
- **我的 fork**：https://github.com/guanowen70-alt/Fashion-AI
- **原始仓库**：https://github.com/liangdabiao/Fashion-AI
- **用途**：全自动 AI 生图流水线。输入新品平铺图，自动在历史爆款库做混合检索（以图搜图 + 销量过滤），找到风格最接近的爆款；随后用 LLM 分析爆款的场景 / 灯光 / 姿势并生成 Prompt，控制 AI 输出专业电商宣传图和模特图。适合跨境电商批量铺货。
- **技术栈**：混合检索、大模型 Prompt 分析、Stable Diffusion。

### 2. 302_ecom_image_generator（电商场景图生成器）
- **我的 fork**：https://github.com/guanowen70-alt/302_ecom_image_generator
- **原始仓库**：https://github.com/302ai/302_ecom_image_generator
- **用途**：专注商品背景替换与重新打光。根据提供的产品图 / 平铺模特图 + 场景描述，在保持产品本身不变形的前提下重新打光、融合，生成色彩一致的高清场景图，同时支持直接生成场景图视频。
- **特点**：提供开箱即用的前端 Web 界面，适合本地自部署修改。

### 3. ecom-details-image（电商详情图生成器）
- **我的 fork**：https://github.com/guanowen70-alt/ecom-details-image
- **原始仓库**：https://github.com/liangdabiao/ecom-details-image
- **用途**：面向电商视觉创作与详情页排版的项目。内置创新的 Campaign Style Lock（品牌风格锁定）机制，输入产品图后，可一键批量输出纯色底主图、场景化生活图、详情页插图、社媒推广图等全套视觉素材。

---

## 二、电商虚拟试衣（Virtual Try-On）与模特替换

### 4. opentryon / OpenTryOn（虚拟试衣工具箱）
- **我的 fork**：https://github.com/guanowen70-alt/opentryon
- **原始仓库**：https://github.com/tryonlabs/opentryon
- **用途**：TryOnLabs 开源的时尚电商 AI 工具箱。提供用于构建虚拟试衣和时尚拍摄（Photoshoots）的开源 API、SDK 和基础模型，允许开发者深度定制服装的材质、褶皱以及模特的动作。

---

## 三、电商短视频、带货视频自动生成

### 5. ClipForge（原名：带货剪手）
- **我的 fork**：https://github.com/guanowen70-alt/clipforge
- **原始仓库**：https://github.com/xixihhhh/clipforge
- **用途**：专为电商打造的 AI 带货短视频神器。商家只需上传一张商品图，AI 就会自动提炼卖点、撰写种草脚本、配音、加字幕，并锁定商品图原图不变形，一键产出符合抖音 / 快手 / 小红书 / TikTok 规格的卖货短视频。支持 0 成本批量出片、开源无水印、本地自部署。
- **技术栈**：ASR / TTS 音频流、LLM 脚本生成、自动化视频剪辑渲染。

### 6. tryon-examples（实时 WebRTC 试衣视频流）
- **我的 fork**：https://github.com/guanowen70-alt/tryon-examples
- **原始仓库**：https://github.com/DecartAI/tryon-examples
- **用途**：由 DecartAI 开源的实时视频虚拟试衣方案。允许消费者在网页端直接打开摄像头（Webcam），通过 WebRTC 技术将衣服 reference 图无缝渲染在实时运动的视频人体上，实现无服务器端延迟的「动态魔镜试衣」。

---

## 备注：PDF 中提到但暂未 Fork 的项目

- **ai-tryon / TryOn AI（生产级虚拟试衣 SaaS，fashion-ecommerce）**：PDF 描述其使用 Next.js (App Router) + PostgreSQL + Google OAuth 登录 + Stripe 积分扣费 + 异步 Webhook 图像交付。该组合特征过于具体，未能检索到精确对应的仓库（候选 `SamurAIGPT/ai-tryon`，但不确定是否同一项目），故暂未 Fork。如需，可告知，我再确认后补 Fork。

---

## 部署建议

若具备一定技术基础，除以上独立项目外，强烈建议搜索并部署 **ComfyUI** 相关生态插件（如 `ComfyUI-IC-Light` 用于产品重新打光、`LayerDiffusion` 用于透明图层生成）。各大工作流分享社区中有大量现成的「电商换背景」「平铺图穿在真人模特身上」的 `.json` 工作流，直接导入即可高精度生产。
