# Immich · Recipkg 配方维护

- 先阅读 `RECIPE.md`、`BUILD_PROMPT.md`、`ACCEPTANCE.md`、`SOURCES.md` 和 `COVERAGE.md`。
- 固定版本是 Immich v3.3.5 提交 `8303cb117e197c700332b33b61b45314c9cc5bb4`；新增行为必须注明版本、来源和观察方法。
- `COVERAGE.md` 中的未知项属于当前范围；不能因实现方便而删除或写成已验证。
- 区分官方文档、固定源码观察、上游运行、独立重建和真实设备验收。
- 配方仓库只提交 UTF-8 Markdown；不得添加上游源码、镜像、模型、二进制、密钥或安装钩子。
- 依赖按实际能力选择。Valkey 和 PostgreSQL 的兼容性缺口必须显式保留。
- 保护未提交工作；打包、`check` 和构建提示词均不代表软件完整。
