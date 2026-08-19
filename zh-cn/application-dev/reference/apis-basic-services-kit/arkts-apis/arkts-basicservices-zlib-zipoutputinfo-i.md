# ZipOutputInfo

压缩和解压缩的返回值信息。

**起始版本：** 23

<!--Device-zlib-interface ZipOutputInfo--><!--Device-zlib-interface ZipOutputInfo-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## 导入模块

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## destLen

```TypeScript
destLen: long
```

目标缓冲区的总长度。

**类型：** long

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ZipOutputInfo-destLen: long--><!--Device-ZipOutputInfo-destLen: long-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## status

```TypeScript
status: ReturnStatus
```

参考[ReturnStatus枚举定义](arkts-basicservices-zlib-returnstatus-e.md)。

**类型：** [ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ZipOutputInfo-status: ReturnStatus--><!--Device-ZipOutputInfo-status: ReturnStatus-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

