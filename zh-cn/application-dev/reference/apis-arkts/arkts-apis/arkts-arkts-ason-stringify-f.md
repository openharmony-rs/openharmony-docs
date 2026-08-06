# stringify

## stringify

```TypeScript
function stringify(value: Object | null | undefined): string
```

该方法将ArkTS对象数据转换为JSON字符串，额外支持Map和Set相关类型。 从API 18开始参数修改为Object类型，API 18之前参数只支持ISendable类型 （除Int8Array、Uint8Array、Int16Array、Uint16Array、Int32Array、Uint32Array、Uint8ClampedArray、Float32Array外）。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ASON-function stringify(value: Object | null | undefined): string--><!--Device-ASON-function stringify(value: Object | null | undefined): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object \| null \| undefined | 是 | ArkTS对象数据。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 18 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 转换后的JSON字符串。 |

