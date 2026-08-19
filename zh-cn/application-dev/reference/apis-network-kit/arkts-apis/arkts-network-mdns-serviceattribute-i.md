# ServiceAttribute

MDNS服务属性信息。

**起始版本：** 10

<!--Device-mdns-export interface ServiceAttribute--><!--Device-mdns-export interface ServiceAttribute-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

## 导入模块

```TypeScript
import { mdns } from '@kit.NetworkKit';
```

## key

```TypeScript
key: string
```

MDNS服务属性键值，键值长度应该小于9个字符。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ServiceAttribute-key: string--><!--Device-ServiceAttribute-key: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

## value

```TypeScript
value: Array<int>
```

MDNS服务属性值。

**类型：** Array&lt;int&gt;

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ServiceAttribute-value: Array<int>--><!--Device-ServiceAttribute-value: Array<int>-End-->

**系统能力：** SystemCapability.Communication.NetManager.MDNS

