# isBuffer

## 导入模块

```TypeScript
import { buffer } from '@kit.ArkTS';
```

<a id="isbuffer"></a>
## isBuffer

```TypeScript
function isBuffer(obj: Object): boolean
```

判断obj是否为Buffer。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function isBuffer(obj: Object): boolean--><!--Device-buffer-function isBuffer(obj: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | Object | 是 | 判断对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果obj是Buffer，则返回true，否则返回false。 |

**示例：**

```TypeScript
import { buffer } from '@kit.ArkTS';

let result = buffer.isBuffer(buffer.alloc(10)); // 10: buffer size
console.info("result = " + result);
// 输出结果：result = true
let result1 = buffer.isBuffer(buffer.from('foo'));
console.info("result1 = " + result1);
// 输出结果：result1 = true
let result2 = buffer.isBuffer('a string');
console.info("result2 = " + result2);
// 输出结果：result2 = false
let result3 = buffer.isBuffer([]);
console.info("result3 = " + result3);
// 输出结果：result3 = false
let result4 = buffer.isBuffer(new Uint8Array(1024));
console.info("result4 = " + result4);
// 输出结果：result4 = false

```

