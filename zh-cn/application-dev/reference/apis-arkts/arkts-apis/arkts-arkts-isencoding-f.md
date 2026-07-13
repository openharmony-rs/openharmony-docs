# isEncoding

## isEncoding

```TypeScript
function isEncoding(encoding: string): boolean
```

判断`encoding`是否为支持的编码格式。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 是 | 编码格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是支持的编码格式返回true，反之则返回false。 |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

console.info(fastbuffer.isEncoding('utf-8').toString());
// 输出结果：true
console.info(fastbuffer.isEncoding('hex').toString());
// 输出结果：true
console.info(fastbuffer.isEncoding('utf/8').toString());
// 输出结果：false
console.info(fastbuffer.isEncoding('').toString());
// 输出结果：false

```

