# FocusedApplicationInfo (获焦应用信息)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

定义获焦应用信息。使用接口[onFocusedApplicationChanged](js-apis-app-ability-appManager.md#appmanageronfocusedapplicationchanged)注册获焦应用变化监听后，当获焦应用变化时，系统通过[FocusedApplicationObserver](js-apis-inner-application-focusedApplicationObserver.md)的[onFocusedApplicationChanged](js-apis-inner-application-focusedApplicationObserver.md#focusedapplicationobserveronfocusedapplicationchanged)回调将获焦应用信息上报给开发者。

## 导入模块

```ts
import { appManager } from '@kit.AbilityKit';
```

## 属性

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| focusedBundleName | string | 否 | 否 | 获焦应用的Bundle名称。 |
| focusedUid | number | 否 | 否 | 获焦应用的uid。 |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let focusedApplicationObserver: appManager.FocusedApplicationObserver = {
  onFocusedApplicationChanged(info: appManager.FocusedApplicationInfo) {
    console.info(`[appManager] onFocusedApplicationChanged: ${JSON.stringify(info)}`);
    console.info(`info.focusedBundleName: ${info.focusedBundleName}`);
    console.info(`info.focusedUid: ${info.focusedUid}`);
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
