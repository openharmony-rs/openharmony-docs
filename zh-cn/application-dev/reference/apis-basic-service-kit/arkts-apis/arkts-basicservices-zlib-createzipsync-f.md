# createZipSync

## createZipSync

```TypeScript
function createZipSync(): Zip
```

创建压缩解压缩对象实例，成功时返回压缩解压缩对象实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-zlib-function createZipSync(): Zip--><!--Device-zlib-function createZipSync(): Zip-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Zip](arkts-basicservices-zlib-zip-i.md) | 返回压缩解压缩对象实例。 |

## 示例

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();
```

