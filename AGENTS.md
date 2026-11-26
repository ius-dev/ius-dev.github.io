<!-- TRELLIS:START -->
# mini-trellis

This project uses mini-trellis as a memory layer. Working knowledge lives under `.trellis/`:

- `.trellis/spec/` — durable contracts (short markdown; read `index.md` first)
- `.trellis/research/` — topic inbox (`<topic>.md`; `README.md` is not a topic)
- `.trellis/workspace/` — per-developer journals

Record a session with `/mini-trellis:remember` (Claude/OpenCode), `/mini-trellis-remember` (Pi/OMP/Kiro/Antigravity/Droid), `$mini-trellis-remember` (Codex/ZCode), or the `mini-trellis-remember` skill (Cursor and DeepSeek Harness). When earlier decisions or relevant project rules are needed, use `mini-trellis mem recall "<topic or path>"`; expand evidence with `mini-trellis mem read "<ref>"`. No search is required for unrelated work. Promote lasting boundaries into spec with `mini-trellis-update-spec`.

When the user confirms or corrects a project rule, save it through remember even without an explicit “remember” request, unless they ask not to save. An agreed future policy is recorded as agreed, not implemented. Also record reusable findings or a useful session/compact handoff. Questions, reviews, ordinary edits and unconfirmed proposals need no new record. New installs write notes without an automatic git commit; use `mini-trellis doctor` to check host wiring and `mini-trellis refresh --dry-run` before refreshing assets.

Keep one current rule in the document that already owns it. Preserve conditions with their rules: “when X, do not Y” must not become “never Y.” Unconfirmed scope, exceptions, and implementation choices stay open or are labeled as inference, not added to the contract.

For a confirmed update, use remember to edit the existing topic, verify the saved section once, record the journal link, and check the new entry/index row. Complete these authorized steps in the same turn without asking again between writes. Reuse returned file contents while unchanged instead of repeating reads. Journal-only success is not topic success; report partial writes accurately. New notes follow the requested or discussion language; updates preserve the document language.

For a memory-only update, reply with one short sentence using actual topic and journal Markdown links; expand for conflicts or partial writes. In a development task, include the links briefly with the requested result. Update affected README/docs/spec/research descriptions, including stale implementation status, in the same turn as the code. This maintenance needs no separate remember request or new journal entry.

When recall excerpts already answer the question with source and qualifiers, cite them and stop. Expand only missing context; do not repeat a lookup or fall back to dialogue-only `search` merely to reconfirm sufficient evidence.

Use project knowledge or supply Markdown/text exports when working with earlier ZCode, Kiro, OMP, or Antigravity conversations. To organize selected past sessions or supplied exports into project knowledge, use `mini-trellis-session-insight`, update existing documents, and preserve sources.

mini-trellis does not create or drive tasks.

Managed by mini-trellis. Edits outside this block are preserved.
<!-- TRELLIS:END -->

## 项目结构约束

本仓库是 ius-dev 的纯静态在线工具集，仓库根目录即站点根目录，推到 `main` 后由 GitHub Pages 直接发布，无构建步骤。

### 目录职责

| 路径 | 职责 | 约束 |
|------|------|------|
| `index.html` | 工具列表首页 | 新增工具必须在此登记卡片 |
| `assets/style.css` | 全站共享样式 | 工具页通用组件只写这里 |
| `assets/favicon.svg` | 站点图标 | — |
| `tools/<工具名>.html` | 单个工具页 | 一页一工具，文件名即访问路径 |
| `.trellis/` | mini-trellis 记忆层 | 生成文件不要手工改写 |

### 硬性约束

1. **逻辑全部在浏览器本地运行**：输入内容不上传、不留存，不引入后端接口、统计或上报脚本。
2. **保持纯静态**：只写 HTML/CSS/JS，不引入构建工具链、包管理或编译步骤，双击 `index.html` 即可打开。
3. **工具页复用现成骨架**：照抄 `tools/xml-unescape.html` 的结构，使用 `.site-header` / `.tool-head` / `.toolbar` / `.panes` / `.pane` / `.tool-footer` 等现有类，不另起样式体系。
4. **通用样式集中管理**：新增的通用样式（例如第三种面板布局）加到 `assets/style.css` 的工具页通用组件区，不得写在单个工具页的 `<style>` 里。
5. **新增工具三处同步**：`tools/` 下新建页面 → `index.html` 的 `.tool-grid` 里加 `<a class="tool-card">` 卡片 → 同页 `.section-title` 的 `<span class="count">` 数字 +1。
6. **统一用相对路径**：页面内引用共享资源写成 `../assets/style.css` 这类相对路径，保证本地直接打开与线上一致。
7. **本文件上方 TRELLIS 区块由 mini-trellis 管理**：手工维护的内容只能写在该区块之外。
