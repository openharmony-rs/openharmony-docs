# restartSelfAtomicService

## 导入模块

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## restartSelfAtomicService

```TypeScript
function restartSelfAtomicService(context: Context): void
```

重启当前原子化服务。

> **说明：**  
>  
> - 当前仅支持以独立窗口方式拉起原子化服务。  
>  
> - 在调用本接口成功后的3秒内，再次调用本接口、  
> [ApplicationContext.restartApp()](arkts-ability-applicationcontext-c.md#restartapp-1)或  
> [UIAbilityContext.restartApp()](arkts-ability-uiabilitycontext-c.md#restartapp-1)接口中的任一接口，系统将返回错误码1  
> 6000064。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-abilityManager-function restartSelfAtomicService(context: Context): void--><!--Device-abilityManager-function restartSelfAtomicService(context: Context): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 当前Ability的上下文。<br>**说明**：当前仅支持[UIAbilityContext](arkts-ability-uiabilitycontext-c.md)。&lt;/br&gt; |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Connect to system service failed;2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000064](../errorcode-ability.md#16000064-重启应用频繁) | Restart too frequently. Try again at least 3s later. |
| [16000086](../errorcode-ability.md#16000086-传入的context不是uiabilitycontext) | The context is not UIAbilityContext. |
| [16000090](../errorcode-ability.md#16000090-调用方不是原子化服务) | The caller is not an atomic service. |

**示例：**

```TypeScript
import { AbilityConstant, EmbeddableUIAbility, Want, abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends EmbeddableUIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // 重启当前原子化服务
      abilityManager.restartSelfAtomicService(this.context);
    } catch (e) {
      console.error(`restartSelfAtomicService error: ${JSON.stringify(e as BusinessError)}`);
    }
  }
}

```

