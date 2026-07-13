# createGZipSync

## createGZipSync

```TypeScript
function createGZipSync(): GZip
```

创建GZip对象。成功时返回GZip对象实例。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| GZip | GZip对象实例。 |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

let gzip = zlib.createGZipSync();

```

