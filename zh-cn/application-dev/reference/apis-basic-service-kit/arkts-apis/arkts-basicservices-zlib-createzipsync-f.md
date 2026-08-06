# createZipSync

## createZipSync

```TypeScript
function createZipSync(): Zip
```

创建压缩解压缩对象实例，成功时返回压缩解压缩对象实例。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-zlib-function createZipSync(): Zip--><!--Device-zlib-function createZipSync(): Zip-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回压缩解压缩对象实例。 |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();
```

