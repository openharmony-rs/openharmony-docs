# isEncoding

## isEncoding

```TypeScript
function isEncoding(encoding: string): boolean
```

判断\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_是否为支持的编码格式。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-fastbuffer-function isEncoding(encoding: string): boolean--><!--Device-fastbuffer-function isEncoding(encoding: string): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 是 | 编码格式，支持的格式范围为[BufferEncoding]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

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

