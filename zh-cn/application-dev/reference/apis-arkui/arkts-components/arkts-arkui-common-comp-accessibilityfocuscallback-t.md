# AccessibilityFocusCallback

```TypeScript
declare type AccessibilityFocusCallback = (isFocus: boolean) => void
```

定义onAccessibilityFocus中使用的回调类型。

@typedef {function} AccessibilityFocusCallback

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isFocus | boolean | 是 | 用于表示组件是否获焦。<br>true：当前组件获焦。<br>false：当前组件失焦。 |
