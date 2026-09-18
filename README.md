# danbooru-tags-data-zh

Danbooru 标签的中文翻译数据库，收录截至 2026 年 8 月图片数量大于 50 的标签，译名以社区通用叫法为准。

同一份数据同时发布在 [GitHub 仓库](https://github.com/amenorira/danbooru-tags-data-zh) 与 [HuggingFace 数据集](https://huggingface.co/datasets/ame-la/danbooru-tags-data-zh)，推送 GitHub 后由 Actions 自动同步。

## 覆盖范围

- 收录 2026 年 8 月时图片数量大于 50 的标签
- 按分类收录：画师（artist）、作品/版权（copyright）、角色（character）、通用（general）、元标签（meta）

当前收录情况：

| 分类 | 标签数 |
| --- | --- |
| 画师 artist | 24881 |
| 作品/版权 copyright | 8413 |
| 角色 character | 35382 |
| 通用 general | 30664 |
| 元标签 meta | 585 |

## 特点

现有的同类数据多为较早期抓取、之后未再更新，且通常只提供单一译名，不含别名，也没有对标签含义的说明。本项目在以下方面做了补充：

- 每个标签附一句注释（notes），说明该标签指代的内容（作品、角色、画师等）。
- 收录常用别名（aliases），包括日文原名、英文名、社区昵称及旧译名。
- 没有通用译名的标签（多见于画师）保留原名，不强行翻译。

## 文件格式

标签按分类存放在 `tags/` 目录，都是 CSV 文件，表头统一：

```
tag, category, aliases, zh, count, notes
```

| 字段 | 说明 |
| --- | --- |
| `tag` | Danbooru 标签原名（小写、下划线分隔） |
| `category` | 标签分类：0 通用 / 1 画师 / 3 作品 / 4 角色 / 5 元标签 |
| `aliases` | 该标签的常用别名，以 `\|` 分隔 |
| `zh` | 简体中文译名；没有通用译名的（多见于画师）保留原名 |
| `count` | 该标签的图片数量（2026 年 8 月） |
| `notes` | 一句话说明该标签指什么 |

## 目录

- `tags/artist.csv` — 画师标签
- `tags/copyright.csv` — 作品/版权标签
- `tags/character.csv` — 角色标签
- `tags/general.csv` — 通用标签
- `tags/meta.csv` — 元标签

## 反馈

如发现译名或注释有误、标签有遗漏，欢迎[提 issue](https://github.com/amenorira/danbooru-tags-data-zh/issues)。

## 许可

本项目采用 MIT 许可发布，详见 [LICENSE](LICENSE)。

## 说明

数据根据 Danbooru 公开的标签信息整理，仅供社区交流与学习使用。