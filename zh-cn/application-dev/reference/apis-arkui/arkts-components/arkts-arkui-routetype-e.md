# RouteType

页面转场类型。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None = 0
```

页面未重定向。如Push和Pop描述中RouteType为None的情形，即页面入场时PageTransitionEnter的转场效果生效；退场时PageTransitionExit的转场效果生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Push

```TypeScript
Push = 1
```

跳转到下一页面，例如从PageA跳转到PageB。对于PageA，指定RouteType为None或Push的PageTransitionExit组件样式生效；对于PageB，指定RouteType为None或Push的PageTransitionEnter组件样式生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Pop

```TypeScript
Pop = 2
```

回退到上一页面，例如从PageB回退到PageA。对于PageB，指定RouteType为None或Pop的PageTransitionExit组件样式生效；对于PageA，指定RouteType为None或Pop的PageTransitionEnter组件样式生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
