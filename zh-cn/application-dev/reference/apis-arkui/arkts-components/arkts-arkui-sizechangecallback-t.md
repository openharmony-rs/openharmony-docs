# SizeChangeCallback

```TypeScript
declare type SizeChangeCallback = (oldValue: SizeOptions, newValue: SizeOptions) => void
```

组件区域变化时的回调类型。

oldValue表示目标元素变化之前的宽高。

newValue表示目标元素变化之后的宽高。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare type SizeChangeCallback = (oldValue: SizeOptions, newValue: SizeOptions) => void--><!--Device-unnamed-declare type SizeChangeCallback = (oldValue: SizeOptions, newValue: SizeOptions) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldValue | [SizeOptions](../arkts-apis/arkts-arkui-sizeoptions-i.md) | 是 |  |
| newValue | [SizeOptions](../arkts-apis/arkts-arkui-sizeoptions-i.md) | 是 |  |

