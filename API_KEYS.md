# 电商 AI 项目 · API Key 注册清单

> 配套 `电商AI开源项目清单.md` 与 `DEPLOY.md`（均在 guanowen70-alt/my-first-project）。
> 7 个项目中，只有 **clipforge** 能 0 Key 免费跑（Openverse 素材 + Edge TTS + 本地 FFmpeg）。
> 其余项目都需要外部 API Key / 数据库 / 显卡才能真正"出图出视频"。
>
> 下面按「去哪个平台注册」分组，每个 Key 能解锁哪些项目一目了然。一个 Key 常能解锁多个项目，不必每个都单独注册。

---

## 一、按平台分组的注册清单

| # | 平台 | 注册地址 | 解锁的项目 | 用途 | 必需度 | 费用 |
|---|---|---|---|---|---|---|
| 1 | **OpenRouter** | https://openrouter.ai/keys | Fashion-AI | 生图流水线的 LLM + 图像模型 | 必需（Fashion-AI） | 按量付费 |
| 2 | **302.ai** | https://302.ai | 302_ecom_image_generator | 电商场景图 / 背景替换 | 必需（302 项目） | 按量付费 |
| 3 | **OpenAI**（或任意 OpenAI 兼容图像 API，如 apimart.ai） | https://platform.openai.com/api-keys | ecom-details-image、opentryon（多选一即可） | 详情图生图、试衣图像 | 必需(ecom-details-image) / opentryon 多选一 | 按量付费 |
| 4 | **Decart** | https://platform.decart.ai | tryon-examples | 实时 WebRTC 试衣视频流 | 必需（tryon-examples） | 按量付费 |
| 5 | **MuAPI** | https://muapi.ai | ai-tryon | SaaS 试衣生图 | 仅 ai-tryon 需要 | 按量付费 |
| 6 | **Stripe** | https://stripe.com | ai-tryon | 支付 / 计费 | 仅 ai-tryon | 免费注册，交易抽成 |
| 7 | **Google Cloud OAuth** | https://console.cloud.google.com | ai-tryon | 登录授权 | 仅 ai-tryon | 免费额度 |
| 8 | **PostgreSQL**（Neon / Supabase） | https://neon.tech 或 https://supabase.com | ai-tryon | 数据库 | 仅 ai-tryon | 有免费层 |
| 9 | **Zilliz Cloud**（向量库） | https://zilliz.com | Fashion-AI（"编码+入库"检索） | 向量检索 | Fashion-AI 配套 | 有免费层 |

---

## 二、opentryon 特殊：多选一即可

opentryon 支持一大堆模型，**最少只需「1 个虚拟试衣服务 + 1 个图像生成服务」**就能跑。可选平台（任选）：

- **虚拟试衣**：Kling AI (klingai.com)、FASHN AI (app.fashn.ai)、Segmind (segmind.com)、Amazon Nova (AWS Bedrock)、Google Vertex…
- **图像生成**：OpenAI、Gemini (aistudio.google.com/app/apikey)、Black Forest Labs / FLUX (bfl.ml)、Luma、Ideogram、Runway、MiniMax、ByteDance Seedance…
- **视频生成**：Kling、Luma、Runway、MiniMax、NVIDIA NIM…

> 省事建议：若已注册 **OpenAI**，就把它作为 opentryon 的图像服务；试衣服务选最便宜的 **FASHN AI** 或 **Kling AI**。

---

## 三、最小集推荐（想"生图 + 视频"都覆盖）

若只想把核心功能跑通，最划算的注册组合：

1. **OpenRouter** → Fashion-AI 生图
2. **302.ai** → 电商场景图
3. **OpenAI** → 详情图 + opentryon 试衣（多选一）
4. **Decart** → 实时试衣视频
5. （可选）**MuAPI** → 想玩 ai-tryon SaaS 再加

`clipforge` **不用注册任何东西**，装好 FFmpeg 直接 `pnpm dev` 就能出带货短视频。

---

## 四、免费路线（不用任何 Key）

- **clipforge**：Openverse 免费素材 + 微软 Edge TTS（keyless）+ 本地 FFmpeg，装好即可 `pnpm dev` 出片。

---

## 五、拿到 Key 后填哪里

| 项目 | 填的文件 | 变量名 |
|---|---|---|
| Fashion-AI | `.env` | `OPENROUTER_API_KEY`（+ Zilliz 的 `MILVUS_HOST` / `MILVUS_TOKEN` 等） |
| 302_ecom_image_generator | `.env` | `NEXT_PUBLIC_API_KEY` |
| ecom-details-image | `.env` | `IMG_API_KEY`（或 `OPENAI_API_KEY` + `OPENAI_BASE_URL` + `OPENAI_IMAGE_MODEL`） |
| opentryon | `.env` | 对应平台变量（如 `OPENAI_API_KEY` / `FASHN_API_KEY` / `GEMINI_API_KEY` …） |
| tryon-examples | 环境变量 | `DECART_API_KEY` |
| ai-tryon | `.env` | `MUAPIAPP_API_KEY` / `STRIPE_*` / `GOOGLE_*` / `DATABASE_URL` |

> 所有 `.env` 都在各自仓库的 `.gitignore` 中，不会被提交。Key 请妥善保管；泄露可随时在对应平台吊销。

---

## 六、快速决策

- 只想**立刻看到效果** → 跑 **clipforge**（零 Key）。
- 想做**电商生图** → 注册 OpenRouter + 302.ai。
- 想做**虚拟试衣/试衣视频** → 注册 Decart（实时视频）+ OpenAI/FASHN（静态试衣）。
- 想搭**完整 SaaS 网站** → 注册 MuAPI + Stripe + Google OAuth + PostgreSQL（ai-tryon，最重）。
