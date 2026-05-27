# wuwa-quest-tracker

鸣潮离线任务统计页面生成器。

本项目用于读取用户自行提供的 SQLite 数据库文件，并生成可直接部署到 GitHub Pages 的静态任务勾选页面。生成结果为自包含 HTML，不依赖后端服务，适合用于查看、搜索和手动标记任务完成情况。

在线页面：<https://wuwa.lyqgzbl.com/quest/>

## 功能特点

- 生成简体中文任务清单页面
- 支持按任务类型浏览任务内容
- 支持在静态页面中手动勾选完成状态
- 输出单个自包含 HTML 文件，便于公开部署
- 仅读取命令行显式传入的数据库路径

## 所需输入

运行前需要自行准备以下文件：

- 任务配置数据库：`db_quest.db`、`db_QuestData.db`、`db_questtype.db`
- 简体中文文本数据库：一个或多个 `lang_multi_text*.db`

## 生成页面

在仓库根目录运行：

```bash
python -m Tools \
  --quest-db /path/to/db_quest.db \
  --questdata-db /path/to/db_QuestData.db \
  --questtype-db /path/to/db_questtype.db \
  --multitext-db /path/to/lang_multi_text.db \
  --multitext-db /path/to/lang_multi_text_1sthalf.db \
  --out docs/quest_tracker_zh.html
```

生成后的页面文件为：

```text
docs/quest_tracker_zh.html
```

## 参数说明

- `--quest-db`：`db_quest.db` 的路径
- `--questdata-db`：`db_QuestData.db` 的路径
- `--questtype-db`：`db_questtype.db` 的路径
- `--multitext-db`：`lang_multi_text*.db` 的路径，可重复传入多个
- `--out`：输出 HTML 路径，默认 `out/quest_tracker_zh.html`
- `--root`：输出根目录，默认当前目录

