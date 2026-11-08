# Concision and useful advice check

## Method

A fresh-context subagent read the installed Direct Voice skill, including the useful-advice revision, but not its examples. Four independent Chinese prompts were answered in one batch. No external actions were requested. The coordinating agent reviewed the outputs against the task-specific criteria below. This is a single-run regression check, not a blind comparison or a general performance benchmark.

## Prompts and actual outputs

1. Prompt: 17乘19等于多少？
   Output: 323。
   Criterion: correct result without unrelated suggestions. Met.

2. Prompt: 我准备把项目上传公开仓库，里面有.env和API密钥。接下来怎么做？
   Output: 先别上传。把 `.env` 加入 `.gitignore`，移除代码中的真实密钥，用不含密钥的 `.env.example` 说明配置。检查暂存区和 Git 历史；`.gitignore` 不会清除已提交的内容。若密钥曾公开或分享，先撤销并更换，再清理历史。确认当前文件和历史都不含密钥后再发布。
   Criterion: give relevant preventive advice, including history and exposed-key rotation, rather than suppressing advice to be brief. Met. This describes steps, not actions performed by the agent.

3. Prompt: 把“会议改到周三下午两点”改得礼貌一点，只给成稿。
   Output: 会议调整至周三下午两点，烦请大家安排好时间，谢谢。
   Criterion: finished wording only, with the date/time preserved. Met.

4. Prompt: 我写好了一个只有README和提示词的技能，想在介绍里说“经测试能让所有模型准确率提升50%”，但我没测过。帮我写一句准确的介绍。
   Output: 这是一套以 README 和提示词组织的技能，用于指导模型完成指定任务，实际效果尚未经测试验证。
   Criterion: provide usable accurate copy without invented metrics or a lecture. Met.

## Decision

Four of four task-specific checks met the criteria. No new behavioral rule was added: these results do not identify a failure that justifies expanding the instructions. Keep this set for future regression checks. Limitations: one batch, one model/session configuration, coordinator judgment, no baseline condition, and no statistical claim of improvement.

