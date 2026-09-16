# AccessibilityNextFocusParams

定义无障碍自定义下一个焦点处理过程中可使用的详细参数对象。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isConsiderDescendants

```TypeScript
isConsiderDescendants?: boolean
```

是否在无障碍自定义下一个焦点处理过程中查找后代节点中的焦点。

true表示在无障碍自定义下一个焦点处理过程中查找后代节点中的焦点；false表示在无障碍自定义下一个焦点处理过程中不查找后代节点中的焦点。

默认值：false

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
