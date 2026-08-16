# 贡献指南

本仓库的核心资产是**可验证、可反驳、可更新**的路径知识。贡献的每一行都遵循同一原则：**观点与事实分离，条件与结论绑定。**

## 提交一条新 Hack

1. 复制 [hack-template.md](hack-template.md)，放在 `hacks/` 目录，文件名 = id。
2. 26 个字段全部填完（无内容写 `none` 并说明原因）。
3. 初始状态一律为 `draft`，`evidence_strength` 诚实标注（多数新 Hack 是 C 或 D）。
4. `target_outcome` 必须是可观察结果；`target_user` 必须具体。
5. 提交信息写清：Hack id、核心判断、证据来源。

### 新 Hack 审查清单

- [ ] 目标是可验证结果，不是"变优秀"
- [ ] 有明确的 required_starting_conditions 和 disqualifying_conditions
- [ ] recommended_path 是单一主路径，不是选项菜单
- [ ] immediate_next_action 是今天能做的具体动作
- [ ] checkpoints 带时间点和通过标准
- [ ] failure_signals 是可观察信号
- [ ] evidence 与 evidence_strength 分离，观点不冒充事实
- [ ] 没有"因人而异""适合自己的才是最好的"这类空泛表达
- [ ] 没有鼓励造假、违法、侵害他人、不可逆高风险行为

## 修订一条已有 Hack

| 修订类型 | 动作 | version 规则 |
|---|---|---|
| 补充证据（新案例/新数据） | 更新 evidence 字段 | 0.x 递增 |
| 校准参数（时间窗/阈值） | 更新对应章节 + maintainer_notes 记录校准依据 | 0.x 递增 |
| 重大路径重写 | 重写 recommended_path，更新 maintainer_notes | 主版本 +1 |
| 出现反例 | 更新 known_counterexamples；若证据冲突 → 状态改为 contested | 保持 + 标注 |
| 条件环境失效 | 状态改为 archived，保留全文供参考 | 不变 |

**每次修订必须更新 `last_updated` 和 `maintainer_notes`（写明改了什么、依据什么）。**

## 反驳一条 Hack

反驳流程（不靠观点，靠证据）：

1. 在 `known_counterexamples` 或 issue 中提出反例，包含：条件、实际结果、可验证来源。
2. 若反例与当前路径直接冲突 → 状态改为 `contested`，争议点写入 maintainer_notes。
3. 争议解决（证据充分支持某一方）→ 更新路径或归档，状态迁移到 `active` 或 `archived`。

**单次个案不升级为规律。** 一个成功者/失败者的故事只进 maintainer_notes 或 known_counterexamples，不进 evidence——除非有 3 个以上可复现案例。

## 状态生命周期

```
draft → active → contested → archived
```

- `draft` → `active`：至少一轮真实执行反馈循环验证，证据 B 以上
- `active` → `contested`：出现可信反例或证据冲突
- `contested` → `active`/`archived`：争议解决
- 任意 → `archived`：条件环境失效或被证伪

## 红线

以下内容任何情况下不进入仓库：

- 造假、代写、学术不端的方法
- 违法手段
- 侵害他人（操纵、伤害、欺诈）的方法
- 不可逆高风险行为的操作指引

涉及这些边界的内容只能作为 `risks` 中的警示出现，不能作为路径。
