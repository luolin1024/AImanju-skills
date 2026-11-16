# AImanju-skills

AI 漫剧/短剧创作技能合集，转个人 skill 的备料库。

## 来源

| 部分 | 来源 | 协议 |
|---|---|---|
| `skills/short-drama*`（12 个） | [zenstory-ai/drama-skills](https://github.com/zenstory-ai/drama-skills) 快照 | MIT（见 `LICENSE`，二次分发须保留） |
| `skills/duanju-pipeline` | 本地自建全链路管线 | 自有 |
| `skills/manju-*`（3 个，2026-11-17） | 本地自建：拆解提炼/换皮编剧/密度压缩 | 自有 |

快照日期：2026-11-16。上游更新：重新 clone 后覆盖 `skills/short-drama*`。

## 结构与分工

```
AImanju-skills/
├── LICENSE                      # 上游 MIT 协议
└── skills/
    ├── duanju-pipeline/         # 【编排层】全链路闭环：选品→拆骨→编剧→制作→复盘
    │   └── references/          #   选品榜单/核心思路卡片/剧本规范(去小说化+爽点节奏)/数据复盘
    └── short-drama*/            # 【执行层】制作链，上游 12 技能
        ├── short-drama          #   项目初始化、路由、创作台
        ├── short-drama-breakdown    # 对标拆解(集长/镜长/对白密度)——duanju-pipeline 环节2可选调用
        ├── short-drama-write        # 单集剧本定稿——环节3交接目标
        ├── short-drama-assets       # 视觉设定拆解
        ├── short-drama-image-prompts / short-drama-storyboard / short-drama-video-prompts
        ├── short-drama-produce      # 付费生成(先预览后确认)
        ├── short-drama-edit         # 剪辑成片(需 ffmpeg)
        ├── short-drama-review       # 审查
        ├── short-drama-develop / short-drama-novel-analyze  # 创意开发/原著拆解
    └── manju-*/                  # 【创作层】本地自建 3 技能，衔接拆解与制作链
        ├── manju-formula         #   拆解→500字总结+最小可抄骨架+结构化公式
        ├── manju-screenplay      #   公式→换皮映射+集数决策+全剧剧本初稿
        └── manju-density         #   剧本信息密度压缩(审计+六手法+指标复检)
```

`duanju-pipeline` 补上游缺口：爆款检索、核心思路层拆解、去小说化硬校验、数据复盘闭环。制作知识单一来源在上游 12 技能，编排层不重复实现。

## 转个人 skill 清单

1. **命名**：`short-drama*` 前缀改成自己的（如 `manju-*`），同步改各 SKILL.md 里的 `$short-drama-*` 交叉引用与 `duanju-pipeline` 环节 4 的编排名单。
2. **描述与调用方式**：逐个过 description——高频用的保留 model-invoked，低频的加 `disable-model-invocation: true` 或并入 router，压上下文负载。
3. **赛道定制**：`duanju-pipeline/references/` 里按自己的赛道改——榜单源换成主攻平台、`analytics.md` 基准值按自己历史数据校准、`core-card.md` 题材类型清单增删。
4. **制作形态**：`short-drama` 的 production_profile/rhythm_profile 默认值按常用画风与视频模型预设。
5. **合规**：保留上游 LICENSE 与各 SKILL.md 的 `license: MIT` 字段；魔改幅度大时在 README 声明 fork 关系。

## 安装回本地

任一技能目录含 `SKILL.md` 即可被识别；转完后拷贝（或软链）到 `~/.agents/skills/<name>/`。
