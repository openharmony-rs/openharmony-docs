# WebDestroyMode

提供SetWebDestroyMode接口配置web组件的销毁模式

**起始版本：** 20

<!--Device-webview-enum WebDestroyMode--><!--Device-webview-enum WebDestroyMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NORMAL_MODE

```TypeScript
NORMAL_MODE = 0
```

普通销毁模式，当web组件触发销毁时，相关资源会在合适的时机释放

**起始版本：** 20

<!--Device-WebDestroyMode-NORMAL_MODE = 0--><!--Device-WebDestroyMode-NORMAL_MODE = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## FAST_MODE

```TypeScript
FAST_MODE = 1
```

快速销毁模式，当web组件触发销毁时，立即释放相关资源

**起始版本：** 20

<!--Device-WebDestroyMode-FAST_MODE = 1--><!--Device-WebDestroyMode-FAST_MODE = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

