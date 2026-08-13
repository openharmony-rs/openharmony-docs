# borderRadiuses

## borderRadiuses

```TypeScript
export declare function borderRadiuses(all: double): NodeBorderRadiuses
```

获取所有边都设置为相同半径的BorderRadiuses对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function borderRadiuses(all: double): NodeBorderRadiuses--><!--Device-unnamed-export declare function borderRadiuses(all: double): NodeBorderRadiuses-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| all | double | 是 | 边框圆角。&lt;br/&gt;单位：vp&lt;br/&gt;。 &lt;br&gt;取值范围：[0, +∞)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodeBorderRadiuses](arkts-na-nodeborderradiuses-t.md) | 边框圆角均设置为传入值的边框圆角对象。 |

