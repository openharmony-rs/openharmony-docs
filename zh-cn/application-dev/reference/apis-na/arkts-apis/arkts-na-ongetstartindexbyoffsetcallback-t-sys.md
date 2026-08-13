# OnGetStartIndexByOffsetCallback（系统接口）

```TypeScript
export type OnGetStartIndexByOffsetCallback = (totalOffset: double) => StartLineInfo
```

根据Grid的总偏移量，计算当前页面起始行的位置，用于快速滑动或反向滑动场景。 **系统接口：** 此接口为系统接口。 **模型约束：** 此接口仅可在Stage模型下使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnGetStartIndexByOffsetCallback = (totalOffset: double) => StartLineInfo--><!--Device-unnamed-export type OnGetStartIndexByOffsetCallback = (totalOffset: double) => StartLineInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| totalOffset | double | 是 | 总滚动偏移量，即Grid当中第一个GridItem的顶部与Grid顶部之间的偏移量。 单位：vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StartLineInfo](arkts-na-grid-startlineinfo-i-sys.md) | - |

