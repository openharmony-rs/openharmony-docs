# printf

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## printf

```TypeScript
function printf(format: string, ...args: Object[]): string
```

通过替换字符串中的占位符进行字符串格式化。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [format](arkts-arkts-util-format-f.md#format)

<!--Device-util-function printf(format: string, ...args: Object[]): string--><!--Device-util-function printf(format: string, ...args: Object[]): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| format | string | 是 | 格式字符串。 |
| args | Object[] | 是 | 用于替换 **format** 中占位符的数据。如果传入 **null**，默认返回第一个参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 包含格式化值的字符串。 |

**示例：**

```TypeScript
let res = util.printf("%s", "hello world!");
console.info(res);
// 输出结果：hello world!

```

