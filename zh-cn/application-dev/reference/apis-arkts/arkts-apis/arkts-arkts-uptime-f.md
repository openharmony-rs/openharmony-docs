# uptime

## uptime

```TypeScript
function uptime(): number
```

获取当前系统已运行的时间（以秒为单位）。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前系统已运行的时间。单位：秒。 |

**示例：**

```TypeScript
let time = process.uptime();

```

