# AutoStartupInfo (系统接口)

定义开机自启动应用组件信息。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 11 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - 本模块接口为系统接口。

## 属性

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称                        | 类型                                 | 只读 | 可选 | 说明                                                         |
| --------------------------- | ------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| bundleName                  | string                               | 否   | 否   | 应用程序的Bundle名称。<br>**ArkTS-Dyn起始版本：** 11<br/>**ArkTS-Sta起始版本：** 23 |
| moduleName                  | string                               | 否   | 是   | 应用程序的Module名称。<br>**ArkTS-Dyn起始版本：** 11<br/>**ArkTS-Sta起始版本：** 23 |
| abilityName                 | string                               | 否   | 否   | 应用程序的Ability名称。<br>**ArkTS-Dyn起始版本：** 11<br/>**ArkTS-Sta起始版本：** 23 |
| abilityTypeName             | string                               | 否   | 是   | 应用程序的Ability类型。<br>**ArkTS-Dyn起始版本：** 11<br/>**ArkTS-Sta起始版本：** 23 |
| appCloneIndex<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否   | 是   | 分身应用索引。<br>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 23 |
| userId<sup>20+</sup>        | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 是   | 应用程序的用户ID。<br>**ArkTS-Dyn起始版本：** 20<br/>**ArkTS-Sta起始版本：** 23 |
| setterUserId<sup>20+</sup>  | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 是   | 将此应用设置为开机自启动的用户ID。<br>**ArkTS-Dyn起始版本：** 20<br/>**ArkTS-Sta起始版本：** 23 |
| canUserModify<sup>20+</sup> | boolean                              | 是   | 是   | 表示是否允许开发者修改此应用的开机自启动状态。<br>**ArkTS-Dyn起始版本：** 20<br/>**ArkTS-Sta起始版本：** 23 |

**示例：**

```ts
import { autoStartupManager, common } from '@kit.AbilityKit';

autoStartupManager.setApplicationAutoStartup({
  bundleName: 'com.example.autostartupapp',
  moduleName: 'entry',
  abilityName: 'EntryAbility',
  abilityTypeName: 'ServiceExtension'
} as common.AutoStartupInfo, (err) => {
  if (err) {
    console.error(`setApplicationAutoStartup failed, err code: ${err.code}, err msg: ${err.message}.`);
    return;
  }
  console.info(`setApplicationAutoStartup success.`);
});
```

