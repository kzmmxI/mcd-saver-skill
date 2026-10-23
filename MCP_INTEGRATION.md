# MCP 集成说明

## 使用的 MCP Server
- 名称：mcd-mcp
- 提供方：麦当劳中国官方 MCP（GitHub: M-China/mcd-mcp-server）
- 接入地址：`https://open.mcd.cn/mcp`（Streamable HTTP）
- 鉴权：Bearer Token，由环境变量 `MCD_MCP_TOKEN` 注入
- 配置示例见 `mcp-config.example.json`

> ⚠️ 注意：部分文档示例写成 `https://mcp.mcd.cn`，实测会返回 401；可用地址为 `https://open.mcd.cn/mcp`。

## 实际使用的 Tool 与业务价值
| 工具 | 用途 | 在 Skill 中的业务价值 |
|------|------|----------------------|
| query-nearby-stores | 查附近门店 | 帮用户定位最近门店 |
| available-coupons | 查可领优惠券 | 省钱核心：找出能薅的券 |
| query-store-coupons | 查门店券 | 补充门店级优惠 |
| query-meals / query-meal-detail | 菜单与详情 | 取单价、算组合 |
| calculate-price | 算价 | 估算套餐到手价 |
| list-nutrition-foods | 营养数据 | 减脂期低卡建议 |
| campaign-calendar | 活动日历 | 不错过限定活动 |

## 调用流程（以"到手价"为例）
1. 用户提问想点的餐品 → `query-meal-detail` 取单价
2. `calculate-price` 计算套餐基准价
3. `available-coupons` + `query-store-coupons` 取可用券
4. 叠加估算到手价并标注"以官方实时为准"
5. 输出口语化建议，全程不调用下单类工具

## 业务价值总结
把分散的"门店 / 券 / 价 / 营养 / 活动"工具编排成一个"省钱参谋"，让用户一句话拿到可执行的省钱方案，降低使用门槛，体现 MCP 编排价值。
