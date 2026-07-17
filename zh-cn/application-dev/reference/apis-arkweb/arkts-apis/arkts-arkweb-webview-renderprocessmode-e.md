# RenderProcessMode

Defines the render process mode.

**起始版本：** 12

<!--Device-webview-enum RenderProcessMode--><!--Device-webview-enum RenderProcessMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SINGLE

```TypeScript
SINGLE = 0
```

ArkWeb single rendering subprocess mode. In this mode, multiple Web pages reuse a rendering subprocess.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderProcessMode-SINGLE = 0--><!--Device-RenderProcessMode-SINGLE = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## MULTIPLE

```TypeScript
MULTIPLE = 1
```

ArkWeb multi-rendering subprocess mode. In this mode, there is one rendering subprocess per Web.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderProcessMode-MULTIPLE = 1--><!--Device-RenderProcessMode-MULTIPLE = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

