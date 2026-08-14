# createGZip

## createGZip

```TypeScript
function createGZip(): Promise<GZip>
```

创建GZip对象。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-zlib-function createGZip(): Promise<GZip>--><!--Device-zlib-function createGZip(): Promise<GZip>-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[GZip](arkts-basicservices-zlib-gzip-i.md)&gt; | Promise对象。返回GZip对象实例。 |

## 示例

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

zlib.createGZip().then((data) => {
  console.info('createGZip success');
})
```

