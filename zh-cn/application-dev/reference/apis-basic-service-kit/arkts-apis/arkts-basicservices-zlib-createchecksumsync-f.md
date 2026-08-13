# createChecksumSync

## createChecksumSync

```TypeScript
function createChecksumSync(): Checksum
```

创建校验对象。成功时返回Checksum对象实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-zlib-function createChecksumSync(): Checksum--><!--Device-zlib-function createChecksumSync(): Checksum-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Checksum](arkts-basicservices-zlib-checksum-i.md) | 校验对象实例。 |

## 示例

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

let checksum = zlib.createChecksumSync()
```

