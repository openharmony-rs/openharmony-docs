# @ohos.app.agent.AgentUIExtensionAbility(带界面的智能体扩展组件)

## 约束限制

- 同一个拉起方在同一时间内最多只能拉起来自同一个提供方的5个AgentUIExtensionAbility实例。  
 - AgentUIExtensionAbility内的窗口和ArkUI组件均不允许创建子窗口，也不支持在子窗口中显示。

## 导入模块

```TypeScript
import { AgentUIExtensionAbility } from '@kit.AbilityKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AgentUIExtensionAbility](arkts-ability-app-agent-agentuiextensionability-agentuiextensionability-c.md) | AgentUIExtensionAbility继承自[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)，为开发者提供接入端侧Agent UI界面显示能力。 |
