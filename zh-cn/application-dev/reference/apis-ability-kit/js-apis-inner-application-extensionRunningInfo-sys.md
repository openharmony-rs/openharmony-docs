# ExtensionRunningInfo (系统接口)

ExtensionRunningInfo模块封装了Extension运行的相关信息，可以通过[getExtensionRunningInfos接口](js-apis-app-ability-abilityManager-sys.md#getextensionrunninginfos)获取。

> **说明：**
>
>  - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> 
>  - 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>  - 本模块接口为系统接口。

## 导入模块

```ts
import { abilityManager } from '@kit.AbilityKit';
```

## 使用说明

导入abilityManager模块，通过调用abilityManager中的方法获取ExtensionRunningInfo。

## 属性

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| extension | [ElementName](js-apis-bundleManager-elementName.md) | 否 | 否 | Extension信息。 |
| pid | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否 | 否 | 进程ID。 |
| uid | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否 | 否 | 应用程序的uid。 |
| processName | string | 否 | 否 | 进程名称。 |
| startTime | ArkTS-Dyn: number<br/>ArkTS-Sta: long | 否 | 否 | Extension被启动时的时间戳。 |
| clientPackage | Array&lt;String&gt; | 否 | 否 | 表示当期进程下的所有包名。 |
| type | [bundle.ExtensionAbilityType](js-apis-bundleManager.md#extensionabilitytype) | 否 | 否 | Extension类型。 |

**示例：**

```ts
import { abilityManager } from '@kit.AbilityKit';

let upperLimit = 1;

function getExtensionInfos() {
  abilityManager.getExtensionRunningInfos(upperLimit, (error, data) => {
    if (error) {
      console.error(`getForegroundApplications failed, error.code: ${error.code}, error.message: ${error.message}`);
      return;
    }

    if (!data || data.length === 0) {
      console.info('No extension running infos available');
      return;
    }

    for (let i = 0; i < data.length; i++) {
      let extensionRunningInfo = data[i];
      console.info(`extensionRunningInfo.extension: ${extensionRunningInfo.extension}`);
      console.info(`extensionRunningInfo.pid: ${extensionRunningInfo.pid}`);
      console.info(`extensionRunningInfo.uid: ${extensionRunningInfo.uid}`);
      console.info(`extensionRunningInfo.processName: ${extensionRunningInfo.processName}`);
      console.info(`extensionRunningInfo.startTime: ${extensionRunningInfo.startTime}`);
      console.info(`extensionRunningInfo.clientPackage: ${extensionRunningInfo.clientPackage}`);
      console.info(`extensionRunningInfo.type: ${extensionRunningInfo.type}`);
    }
  });
}
```

