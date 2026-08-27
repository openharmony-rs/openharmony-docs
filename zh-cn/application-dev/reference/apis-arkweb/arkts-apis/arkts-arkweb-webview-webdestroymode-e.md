# WebDestroyMode

Web组件的销毁模式，当Web组件销毁时，销毁模式会影响Web内核的资源释放时机，例如JavaScript运行上下文、渲染上下文等等。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## NORMAL_MODE

```TypeScript
NORMAL_MODE = 0
```

普通模式，由系统决定Web组件资源的销毁时机。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## FAST_MODE

```TypeScript
FAST_MODE = 1
```

快速模式，当Web组件触发销毁时，立即销毁相关的内部资源。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core
