# createGZip

## createGZip

```TypeScript
function createGZip(): Promise<GZip>
```

创建GZip对象。使用Promise异步回调。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;GZip&gt; | Promise对象。返回GZip对象实例。 |

**示例：**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

zlib.createGZip().then((data) => {
  console.info('createGZip success');
})

```

