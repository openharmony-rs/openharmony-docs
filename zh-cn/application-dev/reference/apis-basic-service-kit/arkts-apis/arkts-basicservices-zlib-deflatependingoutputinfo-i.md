# DeflatePendingOutputInfo

压缩等待返回信息。

**起始版本：** 12

<!--Device-zlib-interface DeflatePendingOutputInfo--><!--Device-zlib-interface DeflatePendingOutputInfo-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## 导入模块

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## bits

```TypeScript
bits: number
```

已生成的输出位数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeflatePendingOutputInfo-bits: int--><!--Device-DeflatePendingOutputInfo-bits: int-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## pending

```TypeScript
pending: number
```

已生成的输出字节数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeflatePendingOutputInfo-pending: int--><!--Device-DeflatePendingOutputInfo-pending: int-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## status

```TypeScript
status: ReturnStatus
```

参考[ReturnStatus枚举定义](arkts-basicservices-zlib-returnstatus-e.md)。

**类型：** ReturnStatus

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DeflatePendingOutputInfo-status: ReturnStatus--><!--Device-DeflatePendingOutputInfo-status: ReturnStatus-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

