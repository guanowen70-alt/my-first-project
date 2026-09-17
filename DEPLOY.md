# 7 个电商 AI 项目 · 本地部署指南

> 配套 `电商AI开源项目清单.md`（在 guanowen70-alt/my-first-project）。本文档记录每个项目的**本地克隆后如何安装、配置、启动**。
> 所有仓库已克隆在 `ecom-ai-projects/` 目录下。
>
> ⚠️ 重要前提：这类 AI 项目几乎都需要**外部 API Key / 数据库 / 显卡**才能真正"出图出视频"。下面每个项目都标注了「实际需要什么」。**不填 Key 也能跑起来的只有 clipforge 的免费路径**（用 Openverse 免费素材 + Edge TTS + 本地 FFmpeg）。

---

## 0. 公共环境准备

- **Git 代理**（本机走 FlClash）：`git config --global http.proxy http://127.0.0.1:7890`
- **Python 3.10+**：用托管版 `C:\Users\km10\.workbuddy\binaries\python\versions\3.13.12\python.exe`，建议每个项目建独立 venv。
- **Node.js 18+**：用托管版 `C:\Users\km10\.workbuddy\binaries\node\versions\22.22.2\node.exe`；前端项目多用 **pnpm**（先 `corepack enable`）。
- **FFmpeg**：clipforge / 视频类必须，`winget install ffmpeg` 或官网下载加入 PATH。

---

## 1. Fashion-AI（电商生图爆款流水线）— Python
- 栈：Python 3.10+，`main.py` CLI，依赖 OpenRouter LLM + 图像模型。
- 安装：`cd Fashion-AI && pip install -r requirements.txt`
- 配置：复制 `.env.example` → `.env`，填 `OPENROUTER_API_KEY`（https://openrouter.ai/keys）。
- 运行：
  ```
  python main.py setup                       # 建库 + 编码 + 入库
  python main.py search --new-id NEW001      # 测试检索
  python main.py generate --new-id NEW001    # 完整生图流水线
  ```
- 需要：OpenRouter API Key（付费按量）。

## 2. 302_ecom_image_generator（电商场景图生成器）— Node/Next.js
- 栈：Next.js，用 **pnpm**。
- 安装：`cd 302_ecom_image_generator && pnpm install`
- 配置：复制 `.env.example` → `.env`，填 302.ai 的 API KEY。
- 运行：`pnpm dev`（开发）｜ 打包部署：`docker build -t ecom_image_generator . && docker run -p 3000:3000 ecom_image_generator`
- 需要：302.ai API Key。

## 3. ecom-details-image（电商详情图生成器）— Python「技能」
- 栈：纯 Python 标准库脚本，**零依赖**；本质是给 Claude Code / Codex / OpenClaw 用的 Skill。
- 前置：Python 3.10+，以及 OpenAI 兼容的「图像生成」API Key。
- 配置：在项目根建 `.env`，填 `IMG_API_KEY=sk-...`（兼容别名 `OPENAI_API_KEY` / `OPENAI_BASE_URL` / `OPENAI_IMAGE_MODEL`）。
- 运行（直接生图脚本）：
  ```
  python3 .claude/skills/ecom-details-image/scripts/generate_image.py --env-file .env ...
  ```
  或在 Claude Code / Codex 中作为 skill 调用。
- 特点：不内置 Key；无 Key 时仍能生成 Prompt，有 Key 才能直接出图。

## 4. opentryon / OpenTryOn（虚拟试衣工具箱）— Python
- 栈：Python 包（PyPI `opentryon`），含 CLI / Python API / MCP Server / Next.js TryOn Studio。
- 安装（conda 推荐）：
  ```
  cd opentryon
  conda env create -f environment.yml && conda activate opentryon
  pip install -e .
  ```
  或 `pip install -r requirements.txt && pip install -e .`
- 配置：`cp env.template .env`，按需填各类模型 Key（如 `BFL_API_KEY`）。
- 试运行（**不花钱**）：
  ```
  python -m tryon.cli.runner.invoke_model --dry-run ...
  ```
- 需要：按所用模型不同，可能需要对应平台 Key；本地/GPU 模型可选 `pip install opentryon[local]`。

## 5. clipforge（带货剪手，电商短视频）— Node/Next.js ✅ 可免费跑
- 栈：Next.js，**必须用 pnpm**（不要用 npm）。
- 安装：
  ```
  cd clipforge
  corepack enable          # 启用 pnpm
  pnpm install
  ```
- 配置：右上角「设置」里填 AI 平台 Key（推荐 Atlas Cloud，一个 Key 同时支持 LLM+生图+生视频）。
  **免费路径（0 Key）**：用 Openverse 免费素材 + 微软 Edge TTS（keyless）+ 本地 FFmpeg 即可出整片，无需任何 Key。
- 运行：
  ```
  pnpm dev                 # 开发服务器，默认 http://localhost:3000
  # 或 Docker 一键：
  docker run -d -p 3000:3000 -v clipforge-data:/data ghcr.io/xixihhhh/clipforge
  ```
- 命令行出片示例：`node bin/clipforge.mjs create --topic "在家手冲咖啡" --quality hd --bgm`
- 需要：本机 **FFmpeg**；要 AI 生图/生视频才需 Key。

## 6. tryon-examples（Decart 实时 WebRTC 试衣视频流）— Next.js
- 栈：7 个独立 Next.js 示例，每个自包含。
- 前置：Node.js 18+，**Decart API Key**（https://platform.decart.ai）。
- 运行（以某个示例为例）：
  ```
  cd tryon-examples/examples/ecommerce
  export DECART_API_KEY="your-api-key"
  npm install && npm run dev
  ```
- 需要：Decart 账号 + API Key（实时试衣走 Decart 云端模型）。

## 7. ai-tryon / TryOn AI（生产级虚拟试衣 SaaS）— Next.js + Postgres + Stripe
- 栈：Next.js App Router，Prisma + PostgreSQL，Stripe 计费，OAuth 登录，MuAPI 生图。
- 安装：`cd ai-tryon && npm install`
- 配置：`cp .env.example .env`，填：
  - `STRIPE_SECRET_KEY` / `NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY`（Stripe 后台）
  - `MUAPIAPP_API_KEY`（muapi.ai）
  - Google OAuth 凭据、`DATABASE_URL`（PostgreSQL）
- 初始化数据库 + 启动：
  ```
  npx prisma generate
  npx prisma db push
  npm run dev
  ```
- 需要：PostgreSQL 实例、Stripe 账号、MuAPI Key、Google OAuth——**最重的一个**，适合学整套 Web 部署。

---

## 快速验证清单（按"能否免费跑"排序）
1. ✅ clipforge — 装 FFmpeg + pnpm install 后即可 `pnpm dev` 免费出片。
2. 🟡 opentryon — `pip install -e .` 后 `--dry-run` 验证 CLI，真实试衣需 Key。
3. 🔑 其余 5 个 — 均需对应平台 API Key / 数据库才能产生实际输出。

> 提示：所有 `.env` / `.env.*` 已各自在 `.gitignore` 中，不会被提交。Key 请自行填写，勿泄露。
