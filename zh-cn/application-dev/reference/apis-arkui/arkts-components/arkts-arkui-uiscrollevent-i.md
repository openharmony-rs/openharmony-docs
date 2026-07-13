# UIScrollEvent

定义UIScrollEvent，用于设置目标组件的不同通用事件。

**继承/实现关系：** UIScrollEvent extends [UIScrollableCommonEvent](arkts-arkui-uiscrollablecommonevent-i.md)

**起始版本：** 19

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setOnDidScroll

```TypeScript
setOnDidScroll(callback: ScrollOnScrollCallback | undefined): void
```

设置或重置Scroll滚动时触发的回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | ScrollOnScrollCallback \| undefined | 是 | 回调函数，在Scroll滚动时触发。 |

## setOnWillScroll

```TypeScript
setOnWillScroll(callback: ScrollOnWillScrollCallback | undefined): void
```

设置或重置Scroll滚动前触发的回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | ScrollOnWillScrollCallback \| undefined | 是 | 回调函数，在Scroll即将滚动时触发。 |

