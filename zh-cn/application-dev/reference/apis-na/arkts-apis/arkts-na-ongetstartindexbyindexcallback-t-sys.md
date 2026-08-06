# OnGetStartIndexByIndexCallback（系统接口）

```TypeScript
export type OnGetStartIndexByIndexCallback = (targetIndex: int) => StartLineInfo
```

根据指定的目标索引，计算Grid滚动到该位置时页面内对应的起始行，用于支持[scrollToIndex]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_等操作。 **系统接口：** 此接口为系统接口。 **模型约束：** 此接口仅可在Stage模型下使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnGetStartIndexByIndexCallback = (targetIndex: int) => StartLineInfo--><!--Device-unnamed-export type OnGetStartIndexByIndexCallback = (targetIndex: int) => StartLineInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetIndex | int | 是 | 要滚动到的目标GridItem的索引。 \_\_\_HTML\_TAG\_USD\_0\_\_\_取值限定为整数。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | - |

