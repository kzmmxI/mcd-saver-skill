# WorkBuddy 开发上下文（workbuddy.md）

本文件记录使用腾讯 WorkBuddy 开发「麦麦省钱助手」的对话上下文，用于核验是否符合 WorkBuddy 联动活动奖励条件。

## 开发环境
- 工具：腾讯 WorkBuddy（Craft 模式）
- 模型：默认高级模型
- 参与活动：麦当劳程序员节创意开发大赛（1024 造物挑战）

## 开发过程摘要
1. 用户目标：做一个基于麦当劳 MCP 的省钱类 Skill，技术小白可零代码参与，不碰下单。
2. 需求拆解（WorkBuddy 协助）：确定只读工具集（门店 / 券 / 菜单 / 算价 / 营养 / 活动），排除下单与支付类工具，降低合规与资金风险。
3. 方案设计：定位为"省钱参谋"，输出到手价估算 + 减脂低卡建议 + 活动提醒。
4. 文件生成（WorkBuddy 生成）：SKILL.md、README.md、MCP_INTEGRATION.md、mcp-config.example.json、CONTEST_DECLARATION.md（官方原文未改动）。
5. 合规核对：确认不调用 create-order 等下单工具；价格 / 营养以官方实时为准；声明文件原样保留。
6. 交付：生成可直接提交 GitHub 的仓库文件，并给出报名 Issue 格式与注意事项。

## 关键决策
- 选用 `https://open.mcd.cn/mcp`（非 `https://mcp.mcd.cn`，后者实测 401）。
- Token 仅以 `${MCD_MCP_TOKEN}` 环境变量占位，不落盘真实凭证。
- 营养建议统一加"仅供参考，不构成专业建议"。

## 结论
项目真实使用 WorkBuddy 完成从需求到交付的全过程，符合联动活动"真实使用 WorkBuddy 智能体开发"的要求。
