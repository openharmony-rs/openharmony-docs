# isBuffer

## isBuffer

```TypeScript
function isBuffer(obj: Object): boolean
```

判断`obj`是否为FastBuffer。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

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

let result = fastbuffer.isBuffer(fastbuffer.alloc(10)); // 10: fastbuffer size
console.info("result = " + result);
// 输出结果：result = true
let result1 = fastbuffer.isBuffer(fastbuffer.from('foo'));
console.info("result1 = " + result1);
// 输出结果：result1 = true
let result2 = fastbuffer.isBuffer('a string');
console.info("result2 = " + result2);
// 输出结果：result2 = false
let result3 = fastbuffer.isBuffer([]);
console.info("result3 = " + result3);
// 输出结果：result3 = false
let result4 = fastbuffer.isBuffer(new Uint8Array(1024));
console.info("result4 = " + result4);
// 输出结果：result4 = false

```

