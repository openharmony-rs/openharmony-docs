# FocusedApplicationObserver (获焦应用监听器)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

获焦应用监听器，可以作为入参传入[onFocusedApplicationChanged](js-apis-app-ability-appManager.md#appmanageronfocusedapplicationchanged)方法，监听获焦应用变化。

## 导入模块

```ts
import { appManager } from '@kit.AbilityKit';
```

## FocusedApplicationObserver.onFocusedApplicationChanged

onFocusedApplicationChanged(info: FocusedApplicationInfo): void

获焦应用发生变化时执行的回调函数。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| info | [FocusedApplicationInfo](js-apis-inner-application-focusedApplicationInfo.md) | 是 | 获焦应用信息。 |

**示例：**
```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let focusedApplicationObserver: appManager.FocusedApplicationObserver = {
  onFocusedApplicationChanged(info: appManager.FocusedApplicationInfo) {
    console.info(`[appManager] onFocusedApplicationChanged: ${JSON.stringify(info)}`);
  }
};

try {
  const observerId = appManager.onFocusedApplicationChanged(focusedApplicationObserver);
  console.info(`[appManager] observerId: ${observerId}`);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```
