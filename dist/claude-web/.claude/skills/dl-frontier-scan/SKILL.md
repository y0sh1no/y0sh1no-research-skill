---
name: dl-frontier-scan
description: "在已确定方向中查找近期顶会、预印本、强竞争方法及官方实现。Use for frontier scans and recent state-of-the-art literature."
---

# 前沿工作定位

先读取[运行环境](references/library/packaging/runtime/portable.md)。目标是识别当前方向的重要进展及最接近的竞争工作。

## 工作方法

1. 从用户方向提取任务、核心机制、实验设定和时间范围。未指定范围时选适合该方向的近期窗口并说明，保留必要的较早基础工作。
2. 按[检索参考](references/library/shared/literature.md)搜索相应会议论文集、OpenReview、arXiv 和作者项目页。分清主会、workshop、在审、录用与预印本；核对版本日期和首次发表时间。
3. 看摘要/引言建立相关性，再读会影响竞争判断的机制、实验协议和附录。按“解决什么、改变什么、证据是什么、与当前问题多近”提取。
4. 查询官方实现、checkpoint、数据和配置。核对仓库是否确为该论文、代码/模型版本及公开完整度；README 宣传不能替代结果或代码检查。
5. 比较最新工作是否改变了问题定义、可行方法或基线强度。榜单第一名可能使用不同预算/数据，按[评估协议](references/library/shared/data-evaluation.md)解释可比性。

## 交付

给出高相关前沿清单及阅读优先级，优先级说明它将帮助理解机制、选择基线还是排除重复贡献。记录发表状态、可核验来源、实现位置与阅读深度。

可按方法演进梳理：基础方法 → 关键改进 → 当前竞争方案。用户只要大概了解时给出足以建立判断的概览；不把每篇文章都展开成长篇精读。

## 可选协作

按会议/时间、机制或论文与实现检索分工，汇总时校准共同范围与去重。独立核验最接近工作的差异比重复生成排行榜有用。见[协作方法](references/library/shared/collaboration.md)。
