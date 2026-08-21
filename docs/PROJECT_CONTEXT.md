# 项目与服务器上下文

这份文档用于在新对话中快速恢复当前项目背景。文档已脱敏，不包含密码、Token、私钥、Redis 密钥或 API Key。

## 服务器

- 主机名：`racknerd-32650d8`
- SSH 用户：`mjc`
- 系统：Debian GNU/Linux 13 (trixie)
- 架构：`x86_64`
- 内存：约 2.4 GiB
- Swap：约 1.2 GiB
- 根分区：约 43 GiB，总剩余空间约 35 GiB
- Docker：29.1.1
- Docker Compose：v2.40.3
- Git：2.47.3
- 服务器已安装 1Panel
- 服务器已有 1Panel OpenResty 容器，不要删除

## WeChat-AI

GitHub 仓库：<https://github.com/SMNETSTUDIO/WeChat-AI>

服务器目录：`~/apps/WeChat-AI`

容器信息：

- 容器名：`wechat-ai`
- Compose 服务名：`wechat-ai`
- 端口映射：`8787:8787`
- 运行状态：应保持 `healthy`

公网地址：<https://robot.voqz.de>

部署关系：

```text
Cloudflare DNS/HTTPS
  -> 1Panel OpenResty 反向代理
  -> 127.0.0.1:8787
  -> Docker 容器 wechat-ai
```

注意：OpenResty/Nginx 的 upstream 应写成 `127.0.0.1:8787`，不要把 `http://` 写进 upstream 主机值中。

本地健康检查：

```bash
curl -s http://127.0.0.1:8787/health/ready
```

公网健康检查：

```bash
curl -I https://robot.voqz.de/health
```

已知配置状态：

- 服务监听 `0.0.0.0:8787`
- `PUBLIC_BASE_URL` 使用 `https://robot.voqz.de`
- `COOKIE_SECURE=true`
- 本地登录已启用
- 首个用户为管理员
- LinuxDo 登录未启用
- Worker 已启用，Worker ID 为 `racknerd-32650d8`
- Redis 使用 Upstash，已配置
- OpenAI 兼容接口已配置
- 当前模型配置为 `gpt-5.6-terra`

不要展示或提交以下敏感值：`WECHAT_AI_TOKEN`、完整 Redis URL/密码、`LLM_API_KEY`、GitHub Token、Cloudflare Token、1Panel 密码和 SSH 私钥。

## 个人博客

GitHub 仓库：<https://github.com/1UmU/my-blog>

本地目录：`C:\Users\win\my-blog`

正式地址：<https://blog.voqz.de>

技术栈：

- Astro
- TypeScript
- pnpm
- Cloudflare Pages
- Sveltia CMS

Cloudflare Pages：

- 项目名：`my-blog`
- 生产分支：`master`
- 开发分支：`develop`
- 正式域名：`blog.voqz.de`
- 已恢复 GitHub 原生自动部署
- 不要删除现有 `my-blog` 项目
- 不要创建 `my-blog-new`

后台地址：<https://blog.voqz.de/admin/>

后台配置文件：`public/admin/config.yml`

CMS 当前目标仓库和分支：

```yaml
repo: 1UmU/my-blog
branch: master
```

因此后台新增、编辑和删除文章会直接提交到 `master`，然后由 Cloudflare Pages 自动构建发布。

GitHub OAuth Worker：<https://sveltia-cms-auth.2715337042.workers.dev>

OAuth 回调地址：`https://sveltia-cms-auth.2715337042.workers.dev/callback`

博客开发流程：

1. 在 `develop` 开发。
2. 本地运行检查和构建。
3. 推送 `develop` 并确认 GitHub Actions 通过。
4. 合并到 `master`。
5. 等待 Cloudflare Pages 发布正式站。

本地验证命令：

```bash
corepack pnpm check
corepack pnpm build
```

## 游戏项目

### 扫雷

- GitHub：<https://github.com/1UmU/game1>
- 本地目录：`C:\Users\win\minesweeper-web`
- 这是现有扫雷项目，不要覆盖或删除

### 平面肉鸽

- GitHub：<https://github.com/1UmU/plane-roguelike>
- 本地目录：`C:\Users\win\plane-roguelike`
- 默认分支：`master`
- 开发分支：`develop`
- 当前提交：`fd1cc27`
- 当前状态：已完成方案文档，还没有开始写实际游戏代码

方案文档：[`GAME_PLAN.md`](GAME_PLAN.md)

计划技术栈：

- Phaser 3
- TypeScript
- Vite
- pnpm
- Cloudflare Pages

第一阶段 M1：

1. 玩家使用 WASD 移动。
2. 敌人追踪玩家。
3. 玩家朝鼠标方向自动发射子弹。

## 通用分支规则

- `develop`：开发、实验和测试
- `master`：经过验证后的正式发布
- 不要直接在 `master` 上试错
- 后台 CMS 的内容提交例外：它当前直接提交到博客 `master`
- 新功能完成后先在 `develop` 验证，再合并到 `master`

## 新对话启动方式

开始新对话时，先提供本文件，并明确要继续处理的项目：

- `WeChat-AI`
- `my-blog`
- `plane-roguelike`
- `game1` 扫雷

