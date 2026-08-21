# 平面肉鸽

一个以俯视角实时战斗为核心的 2D Roguelite 网页小游戏。

## 项目目标

第一版先完成一个可以反复游玩的单机循环：移动、自动攻击、击杀敌人、获得经验、随机升级、进入下一间房间，最后挑战 Boss。

项目会优先保持为纯前端静态站点，方便部署到 GitHub Pages、Cloudflare Pages 或现有 VPS。第一版不引入账号、数据库和联网对战。

## 当前状态

当前仓库处于设计阶段，详细方案见 [`docs/GAME_PLAN.md`](docs/GAME_PLAN.md)。

## 开发约定

- `develop`：功能开发和测试分支
- `master`：经过验证后发布的正式分支
- 每完成一个可运行的小功能就提交一次，避免大批量修改难以回滚

## 计划技术栈

- Phaser 3
- TypeScript
- Vite
- pnpm
- Cloudflare Pages

## 预期命令

项目脚手架建立后使用：

```bash
pnpm install
pnpm dev
pnpm build
```

构建产物目录为 `dist/`。
