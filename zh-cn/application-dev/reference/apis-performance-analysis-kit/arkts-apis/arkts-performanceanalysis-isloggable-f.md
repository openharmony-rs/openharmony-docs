# isLoggable

## isLoggable

```TypeScript
function isLoggable(domain: number, tag: string, level: LogLevel): boolean
```

在打印日志前调用该接口，用于检查指定领域标识、日志标识和级别的日志是否可以打印。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiLog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domain | number | 是 | 日志对应的领域标识，范围是0x0~0xFFFF，超出范围则日志无法打印。<br/>建议开发者在应用内根据需要自定义划分。 |
| tag | string | 是 | 指定日志标识，可以为任意字符串，建议用于标识调用所在的类或者业务行为。tag长度最多为31字节，超出后会截断，不建议使用中文字符，可能出现乱码或者对齐问题。 |
| level | LogLevel | 是 | 日志级别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果返回true，则该领域标识、日志标识和级别的日志可以打印，否则不能打印。 |

**示例：**

```TypeScript
hilog.isLoggable(0x0001, "testTag", hilog.LogLevel.INFO);

```

