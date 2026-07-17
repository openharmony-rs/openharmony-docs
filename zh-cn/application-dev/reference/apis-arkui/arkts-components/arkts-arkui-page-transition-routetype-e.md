# RouteType

页面转场类型。

**起始版本：** 7

<!--Device-unnamed-declare enum RouteType--><!--Device-unnamed-declare enum RouteType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None = 0
```

页面未重定向。如Push和Pop描述中RouteType为None的情形，即页面进场时PageTransitionEnter的转场效果生效；退场时PageTransitionExit的转场效果生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RouteType-None = 0--><!--Device-RouteType-None = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Push

```TypeScript
Push = 1
```

跳转到下一页面。PageA跳转到下一个新的界面PageB。对于PageA，指定RouteType为None或者Push的PageTransitionExit组件样式生效，对于PageB，指定RouteType为None或者Push的PageTransitionEnter组件样式生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RouteType-Push = 1--><!--Device-RouteType-Push = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Pop

```TypeScript
Pop = 2
```

重定向指定页面。从PageB回退到之前的页面PageA。对于PageB，指定RouteType为None或者Pop的PageTransitionExit组件样式生效，对于PageA，指定RouteType为None或者Pop的PageTransitionEnter组件样式生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RouteType-Pop = 2--><!--Device-RouteType-Pop = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

