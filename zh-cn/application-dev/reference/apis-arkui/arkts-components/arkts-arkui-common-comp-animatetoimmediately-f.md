# animateToImmediately

## animateToImmediately

```TypeScript
declare function animateToImmediately(value: AnimateParam, event: () => void): void
```

提供显式动画立即下发功能。该接口仅支持渲染层上的属性动画提前执行，无法用于UI侧的逐帧动画。建议开发者优先使用[animateTo](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#animateto)，以防止干扰框架的显示时序，避免在动画启动时因状态设置不完整而导致的显示错误。务必确保调用时所有涉及动画的属性值已正确设置，否则动画开始的少量帧可能出现渲染异常。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [AnimateParam](arkts-arkui-animateparam-i.md) | 是 | 设置动画效果相关参数，动画参数将作用于event闭包函数中状态变化产生的过渡动效。各属性的取值范围及含义详见[AnimateParam](arkts-arkui-animateparam-i.md)。animateToImmediately接口对AnimateParam各属性的使用与[animateTo](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#animateto)一致，但仅支持渲染层上的属性动画，无法用于UI侧的逐帧动画。 |
| event | () =&gt; void | 是 | 指定显式动效的闭包函数，闭包中仅支持渲染层上的属性动画相关的状态变化，无法用于UI侧的逐帧动画。在闭包函数中导致的状态变化系统会自动插入过渡动画，动画效果由value参数控制。务必确保调用时所有涉及动画的属性值已正确设置，否则动画开始的少量帧可能出现渲染异常。 |
