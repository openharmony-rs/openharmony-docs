# getChannelId

## getChannelId

```TypeScript
function getChannelId(): string
```

获取应用的预装渠道号。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-customConfig-function getChannelId(): string--><!--Device-customConfig-function getChannelId(): string-End-->

**系统能力：** SystemCapability.Customization.CustomConfig

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 渠道号 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { customConfig } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let channelId: string = customConfig.getChannelId();
    console.info('app channelId is ' + channelId);
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { customConfig } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let channelId: string = customConfig.getChannelId();
    console.info('app channelId is ' + channelId);
  }
}
```

