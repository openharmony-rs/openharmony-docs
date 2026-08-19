# DictionaryOutputInfo

InflateGetDictionary和deflateGetDictionary这两个函数会返回值的相关信息。

**起始版本：** 23

<!--Device-zlib-interface DictionaryOutputInfo--><!--Device-zlib-interface DictionaryOutputInfo-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## 导入模块

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## dictionaryLength

```TypeScript
dictionaryLength: int
```

字典的长度。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DictionaryOutputInfo-dictionaryLength: int--><!--Device-DictionaryOutputInfo-dictionaryLength: int-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## status

```TypeScript
status: ReturnStatus
```

参考[ReturnStatus枚举定义](arkts-basicservices-zlib-returnstatus-e.md)。

**类型：** [ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DictionaryOutputInfo-status: ReturnStatus--><!--Device-DictionaryOutputInfo-status: ReturnStatus-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

