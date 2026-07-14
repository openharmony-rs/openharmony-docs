# DatePickerResult

日期选择器返回的时间格式。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## day

```TypeScript
day?: number
```

选中日期的日。

取值范围：与设置的start、end有关，如果没有设置start、end，取值范围为[1, 31]。

**类型：** number

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month?: number
```

选中日期的月的索引值，索引从0开始，0表示1月，11表示12月。

取值范围：与设置的start、end有关，如果没有设置start、end，取值范围为[0, 11]。

**类型：** number

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year?: number
```

选中日期的年。

取值范围：与设置的start、end有关，如果没有设置start、end，取值范围为[1970, 2100]。

**类型：** number

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

