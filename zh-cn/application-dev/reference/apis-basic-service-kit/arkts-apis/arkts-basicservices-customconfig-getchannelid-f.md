# getChannelId

## 导入模块

```TypeScript
import { customConfig } from '@kit.BasicServicesKit';
```

## getChannelId

```TypeScript
function getChannelId(): string
```

获取应用的预装渠道号。

**起始版本：** 12

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-customConfig-function getChannelId(): string--><!--Device-customConfig-function getChannelId(): string-End-->

**系统能力：** SystemCapability.Customization.CustomConfig

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 渠道号 |

**示例：**

```TypeScript
import { customConfig } from '@kit.BasicServicesKit';

let channelId: string = customConfig.getChannelId();
console.info('app channelId is ' + channelId);

```

