# @ohos.app.ability.contextConstant (Context相关常量)(系统接口)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy; @yangxuguang-huawei; @Luobniz21-->
<!--Designer: @ccllee1; @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

ContextConstant提供Context相关的枚举，包含文件加密分区等级、UIAbility启动后的进程模式等。

**起始版本**：26.0.0

> **说明：**
>
> 本模块接口仅可在Stage模型下使用。
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.app.ability.contextConstant (Context相关常量)](js-apis-app-ability-contextConstant.md)。

## 导入模块

```ts
import { contextConstant } from '@kit.AbilityKit';
```

## ContextType

表示常见Context类型的枚举，用于[contextType](./js-apis-inner-application-context.md#contexttype)接口。

**起始版本**：26.0.0

**原子化服务API**：从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称  | 值 | 说明                                                                                                                   |
|-----| -------- |----------------------------------------------------------------------------------------------------------------------|
| SERVICE_EXTENSION_CONTEXT | 5 | [ServiceExtensionContext](js-apis-inner-application-serviceExtensionContext-sys.md)类型。     |
| UI_SERVICE_EXTENSION_CONTEXT | 6 | [UIServiceExtensionContext](js-apis-inner-application-uiserviceExtensionContext-sys.md)类型。     |
| AUTO_FILL_EXTENSION_CONTEXT | 7 | [AutoFillExtensionContext](js-apis-inner-application-autoFillExtensionContext-sys.md)类型。     |

**示例：**

```ts
import { ServiceExtensionAbility, contextConstant } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryServiceExtAbility extends ServiceExtensionAbility {
  onCreate() {
    hilog.info(0x0000, 'testTag', `%{public}s`, 'Ability onCreate');
    let result = this.context.contextType(contextConstant.ContextType.SERVICE_EXTENSION_CONTEXT);
    hilog.info(0x0000, 'testTag', `match contextType result is:%{public}s`, JSON.stringify(result));
  }
}
```