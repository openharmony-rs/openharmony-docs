# ProcessRunningInfo
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!--deprecated_code_no_check-->

ProcessRunningInfo定义进程运行信息，包括进程ID、应用UID、进程名称及进程中所有运行的Bundle名称等，可以通过appManager中的[getProcessRunningInfos](js-apis-application-appManager.md#appmanagergetprocessrunninginfosdeprecated)方法获取。

> **说明：**
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 从API version 8开始支持，从API version 9开始废弃。建议使用[ProcessInformation<sup>9+</sup>](js-apis-inner-application-processInformation.md)替代。

## 导入模块

```ts
import appManager from '@ohos.application.appManager';
```

## 属性

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| pid | number | 否 | 否 | 进程ID。 |
| uid | number | 否 | 否 | 应用的UID。 |
| processName | string | 否 | 否 | 进程名称。 |
| bundleNames | Array&lt;string&gt; | 否 | 否 | 进程中所有运行的Bundle名称。 |

**示例：**
```ts
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

appManager.getProcessRunningInfos().then((data) => {
    console.info(`success: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
    console.error(`failed: ${JSON.stringify(error)}`);
});
```
