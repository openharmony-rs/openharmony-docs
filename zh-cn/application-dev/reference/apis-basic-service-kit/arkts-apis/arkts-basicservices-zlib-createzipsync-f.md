# createZipSync

## createZipSync

```TypeScript
function createZipSync(): Zip
```

创建压缩解压缩对象实例，成功时返回压缩解压缩对象实例。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Zip | 返回压缩解压缩对象实例。 |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();

```

