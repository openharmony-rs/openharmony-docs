# GzErrorOutputInfo

GzError返回信息。

**起始版本：** 12

<!--Device-zlib-interface GzErrorOutputInfo--><!--Device-zlib-interface GzErrorOutputInfo-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## 导入模块

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## status

```TypeScript
status: ReturnStatus
```

返回zlib文件状态码，参考ReturnStatus的定义。

**类型：** ReturnStatus

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GzErrorOutputInfo-status: ReturnStatus--><!--Device-GzErrorOutputInfo-status: ReturnStatus-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## statusMsg

```TypeScript
statusMsg: string
```

zlib文件上发生的最后一个状态的状态消息。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GzErrorOutputInfo-statusMsg: string--><!--Device-GzErrorOutputInfo-statusMsg: string-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

