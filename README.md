# 昇腾 PD 分离推理压测

这是一份可直接安装到 Codex 的个人测试 skill。它约定了用 AISBench 经 PD 代理测纯 P、纯 D 和完整 PD 的方法，适用于昇腾同构、异构双机复测与结果对照。

- **纯 P** 只输出 1 token，按输入长度、缓存命中率比较 TTFT 和 QPS。
- **纯 D** 用原生生成器预填完整重复前缀，再经代理生成 1024 tokens，报告正式轮实测命中率、TPOT 和吞吐。
- **完整 PD** 走真实 P→D 路径。与纯 P 对比时，按同一场景的实测命中率和平均 TTFT 对齐，再比较 QPS。

每轮按目标负载单独预热。结果按固定的 15 列 TSV 输出，可直接粘贴到 Excel。

将仓库克隆到 Codex 个人 skills 目录下的 `ascend-pd-benchmark`，即可在测试任务中调用 `$ascend-pd-benchmark`。本机也可直接在这个安装目录维护并同步后续验证过的经验。

[测试规则](SKILL.md) · [复测与诊断](references/measure.md) · [交付表头和计算口径](references/results.md)
