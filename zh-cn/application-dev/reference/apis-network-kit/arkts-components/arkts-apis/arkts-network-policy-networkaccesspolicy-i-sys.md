# NetworkAccessPolicy（系统接口）

应用对应的连接网络的策略。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## allowCellular

```TypeScript
allowCellular?: boolean
```

是否允许应用访问蜂窝网络。true表示允许，false表示不允许。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## allowWiFi

```TypeScript
allowWiFi?: boolean
```

是否允许应用访问wifi网络。true表示允许，false表示不允许。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## alwaysAllowCellular

```TypeScript
alwaysAllowCellular?: boolean
```

是否允许应用一直访问蜂窝网络。true表示允许，false表示不允许。

**类型：** boolean

**起始版本：** 18

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## alwaysAllowWiFi

```TypeScript
alwaysAllowWiFi?: boolean
```

是否允许应用一直访问wifi网络。true表示允许，false表示不允许。

**类型：** boolean

**起始版本：** 18

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。
