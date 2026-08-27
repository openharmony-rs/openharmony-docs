# RenderProcessMode

ArkWeb渲染子进程模式类型，可根据应用对内存占用与渲染进程隔离的需求选择对应的模式。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## SINGLE

```TypeScript
SINGLE = 0
```

ArkWeb单渲染子进程模式。该模式下，多个Web复用一个渲染子进程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## MULTIPLE

```TypeScript
MULTIPLE = 1
```

ArkWeb多渲染子进程模式。该模式下，每个Web一个渲染子进程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
