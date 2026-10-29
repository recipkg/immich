# 来源覆盖与验证状态

**状态：提取中；未运行 Immich，未执行上游测试，也未独立重建。**

## 固定来源

- 上游：[immich-app/immich v3.3.5](https://github.com/immich-app/immich/tree/8303cb117e197c700332b33b61b45314c9cc5bb4)，提交 `8303cb117e197c700332b33b61b45314c9cc5bb4`。
- GitHub 仓库元数据于 2026-10-29 查询为 117,548 stars；这是日期快照，不代表质量、完整性或使用量。
- 上游根许可证为 AGPL-3.0。仓库内外的模型、字体、应用商店分发和第三方服务仍须分别核对；本记录不是法律审查。

## 已观察

- 固定提交的 README 功能矩阵列出 Web 与 Mobile 的照片/视频上传、查看、重复资产识别、多用户、相册和共享、RAW、EXIF/地图、元数据/对象/人脸/CLIP 搜索、OAuth、公开分享、收藏和归档等能力。该矩阵是上游声明，不是本次运行验证。
- 固定提交的 `docker/docker-compose.yml` 定义 Immich Server、Machine Learning、Valkey 9 和带 VectorChord/pgvecto.rs 扩展的 PostgreSQL 14。媒体目录和数据库分别挂载；模型缓存单独持久化。Server 与 Machine Learning 默认使用 `release` 标签，数据库与 Valkey 镜像在该文件中带摘要。部署复制该文件时仍需将所有应用镜像解析并锁定到确切版本。
- 固定提交的 Server 控制器源码包含 asset、album、search、shared-link、partner、user-admin、map、person、workflow、database-backup 和 job 等接口家族。本次只检查了部分路由装饰器，没有提炼完整 OpenAPI 请求/响应、角色矩阵或每条错误分支。
- 官方架构文档说明媒体与配置数据持久化在 PostgreSQL 和文件系统；Redis 兼容队列由 BullMQ 使用；机器学习服务独立部署并通过模型完成相关任务。该在线文档可能随上游更新，具体重建仍以固定提交为准。
- 官方移动备份文档描述选择备份相册、基于内容 checksum 去重、默认 Wi-Fi 上传以及可选单向相册同步。官方分享文档区分实例内相册共享、Partner Sharing 和公开链接。
- `recipkg extract` 已生成中文标准分析提示词；软件和依赖的实际行为分析依据固定版本 README、Compose、选定源码与官方文档完成。未检出或未运行的部分保持未知。

## Recipkg 依赖审阅

- `quality` 固定到 Recipkg `7f05425ae9843b7e8ce15cb80917977eedb36bdd` 的 `recipes/software-quality`，用于重建质量与证据合同，不是产品运行时服务。
- `design` 固定到 `recipkg/design-directions` 提交 `6fdba350d1effa2d50dc0185095bb91ca7a699ee`，递归固定 `design-foundations` 提交 `8c5bf1f1e40719789cf51bc0dfd8f5aeecae0538`，用于图片密集型时间线、上传状态、共享权限和多端响应式界面设计；不代表视觉已验收。
- `valkey` 固定到 Recipkg 配方提交 `d735fba86179ecb87a500a80d1d2ebcbfc5a1014`。官方 Compose 确实使用 Valkey 9，但当前 Valkey 配方只观察有限命令和恢复样本，尚未验证 Immich 使用的 BullMQ 队列合同。不能据此断言即插即用。
- Compose 使用专用 PostgreSQL 14 镜像，带 VectorChord/pgvecto.rs 扩展。标准库目前没有覆盖这项组合的配方；此数据库及扩展仍是未解决的重建依赖。

## 未验证与缺口

- 没有启动服务器、Web、移动端、数据库、Valkey 或模型容器；没有访问 demo、上传媒体、运行上游测试或进行浏览器/设备验收。
- 未独立实现任何客户端或服务端；`ACCEPTANCE.md` 是待运行计划，不是通过报告。
- 未完整提炼身份初始化、账号邀请、跨用户权限、所有分享策略、API/OpenAPI、移动平台后台限制、外部库扫描、格式边界、上传恢复、数据库迁移、备份/恢复、缩略图、转码、队列幂等与故障恢复。
- 未验证模型准确率、模型下载与缓存、硬件加速、人员聚类、CLIP、地图数据、性能、规模、隐私或安全。
- 未验证 Valkey 对固定版 BullMQ 调用的兼容性，也没有固定并验收 PostgreSQL/VectorChord/pgvecto.rs 的独立实现。

不能从 README、在线文档、Compose 声明、控制器路由、Recipkg 包检查或依赖存在推断这些缺口已经解决。
