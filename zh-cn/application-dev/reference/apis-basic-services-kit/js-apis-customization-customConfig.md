# @ohos.customization.customConfig (定制配置)

本模块接口为应用提供定制配置的获取能力，如渠道号等。

>  **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { customConfig } from '@kit.BasicServicesKit';
```

## customConfig.getChannelId

getChannelId(): string

根据应用的BundleName获取渠道号。

**原子化服务API：** 从API version 13开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Customization.CustomConfig

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**返回值：**

|  类型  |  说明  |
| ------ | ----- |
| string | 渠道号 |

**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let channelId: string = customConfig.getChannelId();
    console.info('app channelId is ' + channelId);
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let channelId: string = customConfig.getChannelId();
    console.info('app channelId is ' + channelId);
  }
}
```
