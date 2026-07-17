# isBuffer

## 导入模块

```TypeScript
import { fastbuffer } from '@kit.ArkTS';
```

## isBuffer

```TypeScript
function isBuffer(obj: Object): boolean
```

判断`obj`是否为FastBuffer。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-fastbuffer-function isBuffer(obj: Object): boolean--><!--Device-fastbuffer-function isBuffer(obj: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | Object | 是 | 判断对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果obj是FastBuffer，则返回true，否则返回false。 |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let allocResult = fastbuffer.isBuffer(fastbuffer.alloc(10)); // 10: fastbuffer size
console.info('allocResult = ' + allocResult);
// 输出结果：allocResult = true
let fromResult = fastbuffer.isBuffer(fastbuffer.from('foo'));
console.info('fromResult = ' + fromResult);
// 输出结果：fromResult = true
let stringResult = fastbuffer.isBuffer('a string');
console.info('stringResult = ' + stringResult);
// 输出结果：stringResult = false
let arrayResult = fastbuffer.isBuffer([]);
console.info('arrayResult = ' + arrayResult);
// 输出结果：arrayResult = false
let uint8ArrayResult = fastbuffer.isBuffer(new Uint8Array(1024));
console.info('uint8ArrayResult = ' + uint8ArrayResult);
// 输出结果：uint8ArrayResult = false

```

