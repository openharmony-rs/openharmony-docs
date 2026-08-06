# MenuOnAppearCallback

```TypeScript
export type MenuOnAppearCallback = (start: int, end: int) => void
```

自定义选择菜单弹出时触发的回调事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type MenuOnAppearCallback = (start: int, end: int) => void--><!--Device-unnamed-export type MenuOnAppearCallback = (start: int, end: int) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 选中内容的起始位置。  |
| end | int | 是 | 选中内容的终止位置。  |

