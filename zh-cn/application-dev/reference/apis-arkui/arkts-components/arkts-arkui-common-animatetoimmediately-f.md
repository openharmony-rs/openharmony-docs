# animateToImmediately

## animateToImmediately

```TypeScript
declare function animateToImmediately(value: AnimateParam, event: () => void): void
```

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function animateToImmediately(value: AnimateParam, event: () => void): void--><!--Device-unnamed-declare function animateToImmediately(value: AnimateParam, event: () => void): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [AnimateParam](arkts-arkui-common-animateparam-i.md) | 是 | Animation settings. |
| event | () => void | 是 | Closure function that displays the animation. The system automatically inserts a transition animation for state changes caused by the closure function. |

