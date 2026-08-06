# Rating

提供在给定范围内选择评分的组件，通常用于商品评价、内容打分等应用场景。 > **说明：** > - 当Rating的父节点有指定宽高时，需为Rating组件指定宽高，或为父节点设置值为true的[clip]{@link CommonMethod#clip(clip: Optional<boolean>)}属性。

## 子组件 无 ###### 键盘走焦规格 | 按键         | 功能描述                        | |------------|-----------------------------| | Tab        | 组件间切换焦点。                    | | 左右方向键   | 评分预览增加/减少（步长为stepSize），不改变实际分值。 | | Home       | 移动到第一个星星， 不改变实际分值。          | | End        | 移动到最后一个星星， 不改变实际分值。         | | Space/Enter | 将当前预览的评分值设置为实际评分。      |

## Rating

```TypeScript
Rating(options?: RatingOptions)
```

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RatingInterface-(options?: RatingOptions): RatingAttribute--><!--Device-RatingInterface-(options?: RatingOptions): RatingAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 设置评分组件。\_\_\_HTML\_TAG\_USD\_0\_\_\_ 未设置时，则按照RatingOptions中各参数的默认值配置。 |

## 汇总

