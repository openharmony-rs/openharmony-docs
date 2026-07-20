# px2vp

<a id="px2vp"></a>
## px2vp

```TypeScript
declare function px2vp(value: number): number
```

Converts a number in units of px to a number in units of vp.By default, the virtual pixel ratio of the screen where the current UI instance is located is used for conversion.If no UI instance is available, the virtual pixel ratio of the default screen is used instead.

**起始版本：** 11

**废弃版本：** 18

**替代接口：** px2vp

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare function px2vp(value: number): number--><!--Device-unnamed-declare function px2vp(value: number): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | Value range of value: (-∞, +∞). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Value range of the return value: (-∞, +∞). |

