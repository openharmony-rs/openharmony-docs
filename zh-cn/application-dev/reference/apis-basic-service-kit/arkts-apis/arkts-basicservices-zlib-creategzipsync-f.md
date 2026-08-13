# createGZipSync

## createGZipSync

```TypeScript
function createGZipSync(): GZip
```

创建GZip对象。成功时返回GZip对象实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-zlib-function createGZipSync(): GZip--><!--Device-zlib-function createGZipSync(): GZip-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [GZip](arkts-basicservices-zlib-gzip-i.md) | GZip对象实例。 |

## 示例

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

let gzip = zlib.createGZipSync();
```

