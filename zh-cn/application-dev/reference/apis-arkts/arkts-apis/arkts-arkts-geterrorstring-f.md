# getErrorString

## getErrorString

```TypeScript
function getErrorString(errno: number): string
```

获取系统错误码的详细信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [errnoToString](arkts-arkts-errnotostring-f.md#errnotostring-1)

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
let result = util.getErrorString(errnum);
console.info("result = " + result);
// 输出结果：result = operation not permitted

```

