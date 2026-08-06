# isLoggable

## isLoggable

```TypeScript
function isLoggable(domain: int, tag: string, level: LogLevel): boolean
```

在打印日志前调用该接口，用于检查指定领域标识、日志标识和级别的日志是否可以打印。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-hilog-function isLoggable(domain: int, tag: string, level: LogLevel): boolean--><!--Device-hilog-function isLoggable(domain: int, tag: string, level: LogLevel): boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domain | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 日志对应的领域标识，范围是0x0~0xFFFF，超出范围则日志无法打印。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_建议开发者在应用内根据需要自定义划分。 |
| tag | string | 是 | 指定日志标识，可以为任意字符串，建议用于标识调用所在的类或者业务行为。tag长度最多为31字节，超出后会截断，不建议使用中文字符，可能出现乱码或者对齐问题。 |
| level | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 日志级别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果返回true，则该领域标识、日志标识和级别的日志可以打印，否则不能打印。 |

**示例：**

```TypeScript
hilog.isLoggable(0x0001, "testTag", hilog.LogLevel.INFO);
```

