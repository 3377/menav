## {日期时间: YYYY-MM-DD HH:mm:ss}

### 1. 默认页面切换为书签页

**变更类型**：improvement

> **目的**：部署后即展示 `bookmarks.yml` 而不是 `home.yml`，符合书签站点主要使用场景。
> **详细说明**：`templates/pages/index.hbs` 将 `active` 类从 `home` 区块移至 `bookmarks` 区块；`src/script.js` 中 `currentPageId` 默认值、`showPage` 首次调用以及搜索重置时的回退逻辑从 `home` 调整为 `bookmarks`，确保任何交互后仍停留在书签页。
> **变更原因**：之前始终落在首页，无法符合用户希望的“默认进入书签”体验。
> **影响范围**：导航激活状态与搜索回退逻辑依赖 `currentPageId`，已同步调整。
> **API 变化**：无。
> **配置变化**：建议在 `config/user/site.yml` 中将书签导航项置顶并保持 `active: true`，以与前端逻辑一致。
> **性能影响**：无明显影响。

   ```
   templates/pages/index.hbs       // 修改默认 active 的页面容器
   src/script.js                   // 更新 currentPageId、showPage 及搜索重置时的回退
   config/user/site.yml            // 仅建议：书签导航项置顶（用户手动完成）
   ```

### 2. Codelf 文档中文化

**变更类型**：docs

> **目的**：让协作者能直接阅读中文版本的项目说明、开发指南与变更记录模板。
> **详细说明**：`attention.md`、`project.md`、`_changelog.md` 三个文件整体翻译为中文，并补充项目简介、依赖列表、目录注释等实用信息。
> **变更原因**：原文为英文占位符，缺乏实际参考价值，且与当前团队语言不符。
> **影响范围**：仅影响 .codelf 文档阅读。
> **API 变化**：无。
> **配置变化**：无。
> **性能影响**：无。

   ```
   .codelf/attention.md   // 开发指南中文化
   .codelf/project.md     // 项目概览与结构说明中文化
   .codelf/_changelog.md  // 变更模板改为中文并记录本次内容
   ```

### 3. {功能简述}

**变更类型**：{类型: feature/fix/improvement/refactor/docs/test/build}

> **目的**：{该功能的目的}
> **详细说明**：{功能的具体描述}
> **变更原因**：{为何需要此次修改}
> **影响范围**：{可能受影响的其他模块/功能}
> **API 变化**：{若涉及 API，请描述旧/新接口}
> **配置变化**：{环境变量、配置文件是否有调整}
> **性能影响**：{对性能的提升或影响}

   ```
   root
   - pkg    // {类型: add/del/refact/-} {目录作用}
    - utils // {类型: add/del/refact} {文件功能}
   - xxx    // {类型: add/del/refact} {文件功能}
   ```

...