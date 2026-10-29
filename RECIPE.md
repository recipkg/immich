# Immich 自托管照片与视频库配方

```toml
format = "recipkg/1"

[package]
name = "immich"
version = "0.1.0"
kind = "software"
description = "自托管照片与视频管理：上传备份、媒体整理、搜索、分享和多端访问。"
entry = "BUILD_PROMPT.md"

[dependencies.quality]
git = "https://github.com/recipkg/recipkg.git"
rev = "7f05425ae9843b7e8ce15cb80917977eedb36bdd"
subdir = "recipes/software-quality"

[dependencies.design]
git = "https://github.com/recipkg/design-directions.git"
rev = "6fdba350d1effa2d50dc0185095bb91ca7a699ee"

[dependencies.valkey]
git = "https://github.com/recipkg/valkey.git"
rev = "d735fba86179ecb87a500a80d1d2ebcbfc5a1014"
```

来源固定为 [Immich v3.3.5](https://github.com/immich-app/immich/tree/8303cb117e197c700332b33b61b45314c9cc5bb4)，上游根目录许可证为 AGPL-3.0。配方提炼自固定提交的 README、部署文件、选定控制器和官方文档；不包含上游源码、二进制、模型或品牌素材。

目标是可自托管的个人或家庭照片与视频库。用户通过 Web、iOS 或 Android 客户端导入、浏览、搜索、整理和分享媒体；管理员维护账号、存储和后台任务。当前配方处于提取阶段，不能用作完整兼容实现或真实媒体的唯一备份方案。

`quality` 是重建质量与证据合同；`design` 是面向产品任务的视觉方向，并递归包含设计基础。`valkey` 对应固定版官方 Compose 使用的 Valkey 队列服务，但该配方目前仍在提取，尚未覆盖 Immich 所需的 BullMQ 队列兼容性。依赖用途与缺口见 `SOURCES.md` 和 `COVERAGE.md`。

上游 Compose 还依赖 PostgreSQL 扩展镜像、持久媒体目录、模型缓存和平台容器。标准库目前没有覆盖 Immich 数据库要求的 PostgreSQL 配方；不能把质量、设计或 Valkey 配方当成这些运行时服务的替代品。
