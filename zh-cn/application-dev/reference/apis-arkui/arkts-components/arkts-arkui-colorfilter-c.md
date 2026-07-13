# ColorFilter

Defines the ColorFilter object.

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: number[])
```

Creates ColorFilter with 4*5 matrix.

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number[] | 是 | 4*5 color matrix values. The value[m*n] is located in the m row and n column. The matrix is row-first. |

