# is64Bit

## is64Bit

```TypeScript
function is64Bit(): boolean
```

检查运行环境是否为 64 位。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回判断结果。如果运行环境是 64 位则返回 true；否则返回 false。 |

**示例：**

```TypeScript
let result = process.is64Bit();

```

