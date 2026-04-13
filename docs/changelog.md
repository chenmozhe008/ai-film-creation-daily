# Changelog

## 2026-04-13 - 系统优化 v2.1

### SKILL 优化
- SKILL.md 从 1018 行精简至 473 行（-54%）
- 拆分详细参考文档：评分指南、飞书格式规范、状态总览
- 移除重复内容、已取消板块、矛盾状态描述
- 合并 Step 3.4+3.5 为统一的作品/方法专项采集步骤

### GitHub 仓库完善
- 新增 `sources/` 目录：开源全部数据源配置（RSS、X 账号池、关键词、KOL 池）
- 新增 `scripts/push-to-github.sh`：服务端自动推送脚本
- 新增 `.github/workflows/publish-daily.yml`：GitHub Actions 发布工作流
- 新增 `docs/`：系统架构文档、评分指南
- 新增 `CONTRIBUTING.md`：贡献指南
- 增强 `.gitignore`：防止 API 密钥泄露

### 安全加固
- 服务器敏感文件权限收紧（644→600）
- 清理历史备份文件
- workspace .gitignore 阻止凭证文件提交
- 清理 112MB 过期图片资源

### 采集能力
- X/Twitter 账号池扩充至 107+（7 个分类）
- B站采集集成 bili-cli
- 公众号采集支持 Exa 免费搜索
- 国产工具官网 Playwright 渲染采集

## 2026-04-07 - 系统上线 v2.0

- 13 渠道采集架构建立
- 6 角色创作者关联度评分体系
- 飞书文档自动写入 + 总入口索引
- 90+ KOL 监控池
