# 来源与许可记录

## 固定上游

- 项目：[immich-app/immich](https://github.com/immich-app/immich)
- 版本：v3.3.5，发布页：[GitHub Release](https://github.com/immich-app/immich/releases/tag/v3.3.5)
- 固定提交：[`8303cb117e197c700332b33b61b45314c9cc5bb4`](https://github.com/immich-app/immich/tree/8303cb117e197c700332b33b61b45314c9cc5bb4)
- 仓库元数据：2026-10-29 查询到 117,548 stars、AGPL-3.0、GitHub API 源码仓库大小 319,967 KB。星数是快照；仓库大小是 GitHub 元数据，不等同于工作区展开体积。
- 根许可证：[固定提交的 LICENSE](https://github.com/immich-app/immich/blob/8303cb117e197c700332b33b61b45314c9cc5bb4/LICENSE)，声明 GNU AGPL v3。品牌标识、模型、依赖和分发平台的许可须分别核对。

## 固定提交中检查的源码

- [README 功能矩阵与产品组成](https://github.com/immich-app/immich/blob/8303cb117e197c700332b33b61b45314c9cc5bb4/README.md)
- [Docker Compose 服务与挂载](https://github.com/immich-app/immich/blob/8303cb117e197c700332b33b61b45314c9cc5bb4/docker/docker-compose.yml)
- Server 控制器：[`asset`](https://github.com/immich-app/immich/blob/8303cb117e197c700332b33b61b45314c9cc5bb4/server/src/controllers/asset.controller.ts)、[`album`](https://github.com/immich-app/immich/blob/8303cb117e197c700332b33b61b45314c9cc5bb4/server/src/controllers/album.controller.ts)、[`search`](https://github.com/immich-app/immich/blob/8303cb117e197c700332b33b61b45314c9cc5bb4/server/src/controllers/search.controller.ts)
- Server 控制器：[`shared-link`](https://github.com/immich-app/immich/blob/8303cb117e197c700332b33b61b45314c9cc5bb4/server/src/controllers/shared-link.controller.ts)、[`partner`](https://github.com/immich-app/immich/blob/8303cb117e197c700332b33b61b45314c9cc5bb4/server/src/controllers/partner.controller.ts)、[`user-admin`](https://github.com/immich-app/immich/blob/8303cb117e197c700332b33b61b45314c9cc5bb4/server/src/controllers/user-admin.controller.ts)
- 固定版官方 Compose 对应的 [v3.3.5 发布说明](https://github.com/immich-app/immich/releases/tag/v3.3.5)。

## 官方文档参考

以下官方文档在 2026-10-29 查阅；文档页面是在线版本，不保证与固定源码提交同步：

- [开发者架构：机器学习、PostgreSQL 与队列](https://docs.immich.app/developer/architecture/)
- [移动端备份](https://docs.immich.app/features/mobile-backup/)
- [移动应用](https://docs.immich.app/features/mobile-app/)
- [相册与公开分享](https://docs.immich.app/features/sharing/)
- [扩展与缩减部署](https://docs.immich.app/guides/scaling-immich/)
- [升级说明与版本兼容政策](https://docs.immich.app/install/upgrading/)

在线文档用于发现用户流程；冲突时保留版本差异，不将当前网页描述冒充为 v3.3.5 的固定源码证据。

## Recipkg 依赖选择

| 别名 | 固定来源 | 用途与边界 |
| --- | --- | --- |
| `quality` | [`software-quality`](https://github.com/recipkg/recipkg/tree/7f05425ae9843b7e8ce15cb80917977eedb36bdd/recipes/software-quality)，Recipkg 提交 `7f05425ae9843b7e8ce15cb80917977eedb36bdd` | 重建质量、错误恢复、数据完整性与性能证据要求；不是 Immich 运行库。 |
| `design` | [`design-directions`](https://github.com/recipkg/design-directions/tree/6fdba350d1effa2d50dc0185095bb91ca7a699ee)，提交 `6fdba350d1effa2d50dc0185095bb91ca7a699ee` | 选择适合媒体库、多端和共享状态的界面方向；递归包含 `design-foundations` 提交 `8c5bf1f1e40719789cf51bc0dfd8f5aeecae0538`。 |
| `valkey` | [`recipkg/valkey`](https://github.com/recipkg/valkey/tree/d735fba86179ecb87a500a80d1d2ebcbfc5a1014)，提交 `d735fba86179ecb87a500a80d1d2ebcbfc5a1014` | 固定版官方 Compose 使用 Valkey 9；当前配方未验证 Immich/BullMQ 的完整队列合同，依赖仍待验收。 |

依赖按真实配方职责声明，不把类别相近当成接口兼容。标准库当前缺少 PostgreSQL 14、VectorChord 与 pgvecto.rs 的对应配方；此运行时依赖尚未覆盖。
