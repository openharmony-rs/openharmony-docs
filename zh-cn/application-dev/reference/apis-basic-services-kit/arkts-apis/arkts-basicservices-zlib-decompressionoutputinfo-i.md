# DecompressionOutputInfo

解压缩返回信息。

**起始版本：** 23

<!--Device-zlib-interface DecompressionOutputInfo--><!--Device-zlib-interface DecompressionOutputInfo-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## 导入模块

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## destLength

```TypeScript
destLength: long
```

目标缓冲区的总长度。

**类型：** long

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DecompressionOutputInfo-destLength: long--><!--Device-DecompressionOutputInfo-destLength: long-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## sourceLength

```TypeScript
sourceLength: long
```

源缓冲区的长度。

**类型：** long

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DecompressionOutputInfo-sourceLength: long--><!--Device-DecompressionOutputInfo-sourceLength: long-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## status

```TypeScript
status: ReturnStatus
```

参考[ReturnStatus枚举定义](arkts-basicservices-zlib-returnstatus-e.md)。

**类型：** [ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DecompressionOutputInfo-status: ReturnStatus--><!--Device-DecompressionOutputInfo-status: ReturnStatus-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

