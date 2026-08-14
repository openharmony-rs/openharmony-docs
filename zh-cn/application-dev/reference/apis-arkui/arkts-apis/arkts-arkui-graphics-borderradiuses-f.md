# borderRadiuses

## borderRadiuses

```TypeScript
export function borderRadiuses(all: number): BorderRadiuses
```

用于生成边框圆角均设置为传入值的边框圆角对象。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export function borderRadiuses(all: number): BorderRadiuses--><!--Device-unnamed-export function borderRadiuses(all: number): BorderRadiuses-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| all | number | 是 | 边框圆角。 &lt;br&gt;单位：vp &lt;br&gt;取值范围：[0, +∞) &lt;br&gt;负数按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BorderRadiuses](arkts-arkui-borderradiuses-t.md) | 边框圆角均设置为传入值的边框圆角对象。 |

