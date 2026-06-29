# RunningAppClone (系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wendel-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

定义分身应用在运行态的结构信息。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 12 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口为系统接口。

## 使用说明

通过appManager的[getRunningMultiAppInfo](js-apis-app-ability-appManager-sys.md#appmanagergetrunningmultiappinfo12)来获取。

## RunningAppClone

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称                      | 类型   | 只读  | 可选  | 说明       |
| ------------------------- | ------ | ---- |  ---- | --------- |
| appCloneIndex | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否  | 否  | 分身应用的索引。 |
| uid | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否  | 否  | 表示应用程序的UID。 |
| pids | ArkTS-Dyn: Array&lt;number&gt;<br/>ArkTS-Sta: Array&lt;int> | 否  | 否  | 应用的进程ID集合。 |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName: string = 'ohos.samples.etsclock';
  appManager.getRunningMultiAppInfo(bundleName).then((info: appManager.RunningMultiAppInfo) => {
    hilog.info(0x0000, 'testTag', `getRunningMultiAppInfo success`);
  }).catch((error: Error) => {
    let err = error as BusinessError;
    hilog.error(0x0000, 'testTag', `getRunningMultiAppInfo error, code: ${err.code}, msg:${err.message}`);
  })
} catch (error) {
  let err = error as BusinessError;
  hilog.error(0x0000, 'testTag', `getRunningMultiAppInfo error, code: ${err.code}, msg:${err.message}`);
}
```
