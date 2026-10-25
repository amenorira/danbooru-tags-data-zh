# danbooru-tags-data-zh

Danbooru 标签的中文翻译数据库，收录截至 2026 年 8 月图片数量大于 50 的标签，译名以社区通用叫法为准。

同一份数据同时发布在 [GitHub 仓库](https://github.com/amenorira/danbooru-tags-data-zh) 与 [HuggingFace 数据集](https://huggingface.co/datasets/ame-la/danbooru-tags-data-zh)，推送 GitHub 后由 Actions 自动同步。

## 覆盖范围

- 收录 2026 年 8 月时图片数量大于 50 的标签
- 按分类收录：画师（artist）、作品/版权（copyright）、角色（character）、通用（general）、元标签（meta）
- 另收录少量图数不足 50 的标签（含 Danbooru 已废弃者），这些是打标器（如 [pixai-tagger-v1.0](https://huggingface.co/pixai-labs/pixai-tagger-v1.0)）会输出、但尚未达到收录阈值的标签，用以保证打标结果全部可查
- 另收录少量常用于打标的自定义补充标签（如 `three_quarter_view`），在 notes 中注明非 Danbooru 标签，count 填 0

当前收录情况：

| 分类 | 标签数 |
| --- | --- |
| 画师 artist | 24881 |
| 作品/版权 copyright | 8414 |
| 角色 character | 35384 |
| 通用 general | 30693 |
| 元标签 meta | 580 |

## 特点

现有的同类数据多为较早期抓取、之后未再更新，且通常只提供单一译名，不含别名，也没有对标签含义的说明。本项目在以下方面做了补充：

- 为有据可查的标签附一句注释（notes），说明该标签指代的内容（作品、角色、画师等）；查不到可靠信息时留空，不写填充语。
- 收录常用别名（aliases），包括日文原名、英文名、社区昵称及旧译名。
- 没有通用译名的标签（多见于画师）保留原名，不强行翻译。

## 文件格式

标签按分类存放在 `tags/` 目录，都是 CSV 文件，表头统一：

```
tag, category, aliases, zh, count, notes
```

| 字段 | 说明 |
| --- | --- |
| `tag` | Danbooru 标签原名或自定义补充标签名（小写、下划线分隔） |
| `category` | 标签分类：0 通用 / 1 画师 / 3 作品 / 4 角色 / 5 元标签 |
| `aliases` | 该标签的常用别名，以 `\|` 分隔 |
| `zh` | 简体中文译名；没有通用译名的（多见于画师）保留原名 |
| `count` | 该标签的图片数量（2026 年 8 月）；自定义补充标签填 0，不代表实际图数 |
| `notes` | 一句话说明该标签指什么；查不到可靠信息时留空 |

画师类别的 `aliases` 在同一条记录内按 Unicode NFKC 和大小写折叠判重，保留一种原始写法，不改写署名本身；与该条 `tag` 完全相同的值不重复收录。检索时建议对 `tag`、`zh` 和各个别名采用相同的归一化规则。

不同作者可能使用相同的名字或别名，`zh` 和 `aliases` 不保证唯一，应以 `tag` 区分记录；不能仅凭名称重合合并作者。社团集合标签与成员个人标签也分别保留。

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
