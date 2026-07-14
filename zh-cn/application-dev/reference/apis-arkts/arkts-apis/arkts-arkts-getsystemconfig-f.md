# getSystemConfig

## getSystemConfig

```TypeScript
function getSystemConfig(name: number): number
```

获取系统配置信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getSystemConfig](arkts-arkts-processmanager-c.md#getsystemconfig-1)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | number | 是 | 指定系统配置参数名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回系统配置信息。 |

**示例：**

```TypeScript
let _SC_ARG_MAX = 0;
let pres = process.getSystemConfig(_SC_ARG_MAX);

```

