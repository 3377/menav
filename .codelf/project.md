## MeNav 导航站 (根据 README 汇总)

> MeNav 是一个面向个人/团队的静态导航站点生成器，聚焦“零后端、快速部署、模块化配置”。

> 项目目标：提供一套可通过 YAML/书签文件驱动的定制化主页，支持自动构建与在线部署。

> 当前状态：活跃维护中，最新版本 1.3.0，持续迭代 UI/交互与配置体系。

> 核心作者/团队：社区驱动（原作者 rbetree，当前仓库由 3377/menav 维护）。

> 技术栈：Node.js + 原生 JavaScript + Handlebars 模板，使用 YAML 作为配置格式。



## 主要依赖（根据 package.json）

* handlebars (^4.7.8)：模板引擎，负责渲染页面布局
* js-yaml (^4.1.1)：解析 YAML 配置
* ansi-regex / ansi-styles / supports-color / has-flag / color-convert / color-name：命令行输出着色依赖
* mime-db (^1.52.0)：静态资源 MIME 信息
* prettier (^3.4.2)：开发期格式化工具
* serve (^14.2.5)：本地预览静态构建产物


## 开发环境

> Node.js 18+、npm 9+。核心脚本位于 package.json：
> - `npm run dev`：生成并本地预览
> - `npm run build`：清理后重新生成 dist
> - `npm run import-bookmarks`：将 HTML 书签转换为模块化配置
> - `npm run check`：lint + 测试 + 构建一体化检查
> 构建流程直接使用 npm scripts，无额外 Makefile。


## 项目结构（带中文注释）

> 重点目录已补充用途说明，便于后续协作定位。
```
root
- .editorconfig               // 编辑器统一格式设置
- .gitattributes              // Git 属性配置
- .github/workflows           // CI/CD 工作流（ci.yml、deploy.yml）
- .gitignore                  // Git 忽略规则
- .prettierrc.json            // Prettier 风格配置
- .windsurfrules              // Windsurf IDE 规则
- assets/                     // 静态资源与样式
    - menav.svg               // 站点图标
    - pinyin-match.js         // 拼音匹配脚本
    - preview_*.png           // 预览图
    - style.css               // 主题样式
- bookmarks/                  // 书签导入相关文档、占位
- config/                     // 模块化配置入口
    - README.md               // 配置说明
    - user/                   // 用户自定义配置（完全替换策略）
        - pages/*.yml         // 各页面内容（home/bookmarks/projects 等）
        - site.yml            // 站点基本信息与导航
    - _default/               // 官方默认配置，可用于初始化
- LICENSE                     // AGPL 许可证
- licenses/                   // 第三方依赖版权声明
- package.json / lock         // Node 项目依赖与脚本
- README.md                   // 项目文档
- scripts/clean.js            // 构建前清理 dist
- src/                        // 核心 Node 逻辑
    - generator.js            // 主生成器，读取配置渲染模板
    - bookmark-processor.js   // 书签 HTML → YAML 转换
    - script.js               // 前端交互脚本
    - helpers/                // Handlebars 帮助函数集合
- templates/                  // Handlebars 模板
    - layouts/default.hbs     // 主布局
    - pages/*.hbs             // 各页面模板（home/bookmarks 等）
    - components/*.hbs        // 公共组件（导航、分类、搜索结果等）
- test/bookmark-processor.node-test.js // 书签脚本测试
