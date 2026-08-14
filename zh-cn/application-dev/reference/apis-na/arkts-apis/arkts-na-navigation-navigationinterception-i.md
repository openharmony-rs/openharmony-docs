# NavigationInterception

Navigation跳转拦截对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface NavigationInterception--><!--Device-unnamed-export declare interface NavigationInterception-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## didShow

```TypeScript
didShow?: InterceptionShowCallback
```

页面跳转后回调。在该回调中操作栈在下一次跳转中刷新。

**类型：** [InterceptionShowCallback](arkts-na-interceptionshowcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInterception-didShow?: InterceptionShowCallback--><!--Device-NavigationInterception-didShow?: InterceptionShowCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## interception

```TypeScript
interception?: InterceptionCallback
```

页面跳转前的回调，允许操作栈，在当前跳转中生效。拦截的页面不会被创建。 **模型约束：** 此接口仅可在Stage模型下使用。

**类型：** [InterceptionCallback](arkts-na-interceptioncallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInterception-interception?: InterceptionCallback--><!--Device-NavigationInterception-interception?: InterceptionCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## modeChange

```TypeScript
modeChange?: InterceptionModeCallback
```

Navigation单双栏显示状态发生变更时触发该回调。

**类型：** [InterceptionModeCallback](arkts-na-interceptionmodecallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInterception-modeChange?: InterceptionModeCallback--><!--Device-NavigationInterception-modeChange?: InterceptionModeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## willShow

```TypeScript
willShow?: InterceptionShowCallback
```

页面跳转前的回调，允许操作栈，在当前跳转中生效。拦截的页面会被创建。

**类型：** [InterceptionShowCallback](arkts-na-interceptionshowcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationInterception-willShow?: InterceptionShowCallback--><!--Device-NavigationInterception-willShow?: InterceptionShowCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

