# RunningMultiAppInfo (系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wendel-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

定义应用多开在运行态的结构信息，包含应用包名、多开模式（分身模式或多实例模式）及对应的运行实例信息。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 12 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口为系统接口。

## 使用说明

通过appManager的[getRunningMultiAppInfo](js-apis-app-ability-appManager-sys.md#appmanagergetrunningmultiappinfo12)接口获取。该接口根据应用包名查询应用的多开运行态信息，返回的RunningMultiAppInfo结构包含应用的多开模式（[MultiAppMode](js-apis-inner-application-multiAppMode-sys.md#multiappmode)）及对应的运行实例信息：当应用处于分身模式（APP_CLONE）时，runningAppClones字段返回分身应用信息；当应用处于多实例模式（MULTI_INSTANCE）时，runningMultiInstances字段返回多实例应用信息。

## RunningMultiAppInfo

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称                      | 类型   | 只读  | 可选  | 说明       |
| ------------------------- | ------ | ---- | ---- | --------- |
| bundleName | string | 否  | 否  | 应用的包名。<br>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 23 |
| mode | [MultiAppMode](js-apis-inner-application-multiAppMode-sys.md) | 否  | 否  | 应用多开模式。<br>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 23 |
| runningAppClones | Array<[RunningAppClone](js-apis-inner-application-runningAppClone-sys.md)> | 否  | 是  | 特定包名在运行态的分身应用信息。<br>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 23 |
| runningMultiInstances<sup>14+</sup> | Array<[RunningMultiInstanceInfo](js-apis-inner-application-runningMultiInstanceInfo-sys.md)> | 否  | 是  | 特定包名在运行态的多实例应用信息。<br>**ArkTS-Dyn起始版本：** 14<br/>**ArkTS-Sta起始版本：** 23 |

**示例：**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = "ohos.samples.etsclock";
  // 获取应用多开运行态信息
  appManager.getRunningMultiAppInfo(bundleName)
    .then((info: appManager.RunningMultiAppInfo) => {
      console.info(`getRunningMultiAppInfo success, data: ${JSON.stringify(info)}`);
    }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`getRunningMultiAppInfo failed, code: ${err.code}, msg:${err.message}`);
  })
} catch (err) {
  // 处理入参错误异常
  let code = (err as BusinessError).code;
  let msg = (err as BusinessError).message;
  console.error(`getRunningMultiAppInfo error, code: ${code}, msg:${msg}`);
}
```

