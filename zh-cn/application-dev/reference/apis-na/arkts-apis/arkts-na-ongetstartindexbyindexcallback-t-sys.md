# OnGetStartIndexByIndexCallback（系统接口）

```TypeScript
export type OnGetStartIndexByIndexCallback = (targetIndex: int) => StartLineInfo
```

根据指定的目标索引，计算Grid滚动到该位置时页面内对应的起始行，用于支持scrollToIndex等操作。 **系统接口：** 此接口为系统接口。 **模型约束：** 此接口仅可在Stage模型下使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnGetStartIndexByIndexCallback = (targetIndex: int) => StartLineInfo--><!--Device-unnamed-export type OnGetStartIndexByIndexCallback = (targetIndex: int) => StartLineInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetIndex | int | 是 | 要滚动到的目标GridItem的索引。 <br>取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StartLineInfo](arkts-na-grid-startlineinfo-i-sys.md) | - |

