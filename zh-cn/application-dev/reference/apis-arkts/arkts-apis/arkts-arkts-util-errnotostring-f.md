# errnoToString

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

<a id="errnotostring"></a>
## errnoToString

```TypeScript
function errnoToString(errno: number): string
```

获取系统错误码的详细信息。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-util-function errnoToString(errno: number): string--><!--Device-util-function errnoToString(errno: number): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errno | number | 是 | 生成的错误码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 错误码的详细信息。 |

**示例：**

```TypeScript
let errnum = -1; // -1 : a system error number
let result = util.errnoToString(errnum);
console.info("result = " + result);
// 输出结果：result = operation not permitted

```

