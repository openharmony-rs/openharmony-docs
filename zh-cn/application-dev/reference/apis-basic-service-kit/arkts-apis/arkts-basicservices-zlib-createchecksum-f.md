# createChecksum

## createChecksum

```TypeScript
function createChecksum(): Promise<Checksum>
```

创建校验对象。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Checksum&gt; | Promise对象。返回校验对象实例。 |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

zlib.createChecksum().then((data) => {
  console.info('createChecksum success');
})

```

