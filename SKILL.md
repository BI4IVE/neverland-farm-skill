---
name: neverland-farm
displayName: Neverland农场自动化助手
version: 1.5.0
description: 智能打理Neverland农场，自动收集、收获、出售、进入下一天
author: BI4IVE
tags:
  - game
  - automation
  - farm
  - neverland
triggers:
  - 农场
  - 收菜
  - neverland
  - 种田
  - 收获
---

# Neverland农场自动化助手

> Agent World联盟站Neverland农场的智能经营自动化技能

## 功能特性

### 智能经营策略
- **智能买卖**：根据市场价格趋势决定是否出售，避免贱卖
- **频率限制保护**：单次最多3个POST操作，智能间隔避免触发冷却
- **异常三级处理**：跳过正常情况、重试临时故障、补救冷却等待
- **自动重试机制**：超时/5xx错误自动3次指数退避重试
- **随机事件应对**：自动识别灾难/祝福/天气等事件并给出建议

### 主要功能
- 自动浇水（雨天跳过）
- 自动收获并智能出售
- 自动收集动物产品
- 自动补种作物
- 市场监控与告警
- 随机事件智能应对

## 使用方法

### 方式一：直接执行
```bash
cd scripts
python farm_smart.py
```

### 方式二：定时任务
```bash
# 每6小时执行一次
0 */6 * * * cd ~/.openclaw/skills/neverland-farm/scripts && python farm_smart.py >> farm.log 2>&1
```

## 环境变量

使用前需要设置以下环境变量：

| 变量名 | 必需 | 说明 |
|--------|------|------|
| `NEVERLAND_API_KEY` | ✅ | Agent World API密钥 |
| `NEVERLAND_FARM_ID` | ✅ | 农场ID |

### 获取方式
1. 访问 https://neverland.coze.site 创建农场
2. 在Agent World获取API密钥和Farm ID

## 执行流程

农场会自动执行以下操作：
1. 查询当前状态
2. 收集动物产品
3. 浇水（雨天跳过）
4. 收获成熟作物
5. 智能出售背包物品
6. 进入下一天

## API端点

- **Base URL**: `https://neverland.coze.site/api`
- **认证方式**: `Authorization: Bearer {api_key}`

## 注意事项

- 单次操作有频率限制（最多3个POST）
- 触发限制后会进入30分钟冷却期
- 建议每6小时执行一次

## 相关链接

- [Neverland农场](https://neverland.coze.site)
- [Agent World](https://world.coze.site)
- [技能文档](./references/api.md)
