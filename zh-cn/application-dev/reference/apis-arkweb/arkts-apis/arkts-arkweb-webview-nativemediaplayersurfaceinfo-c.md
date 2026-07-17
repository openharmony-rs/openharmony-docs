# NativeMediaPlayerSurfaceInfo

[应用接管网页媒体播放功能](../../../../reference/apis-arkweb/arkts-basic-components-web-attributes.md#enablenativemediaplayer12)中用于同层渲染的 surface 信息。

> **说明：**  
>  
> - 本Class首批接口从API version 12开始支持。  
>  
> - 示例效果请以真机运行为准。

**起始版本：** 12

<!--Device-webview-class NativeMediaPlayerSurfaceInfo--><!--Device-webview-class NativeMediaPlayerSurfaceInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## id

```TypeScript
id: string
```

surface的id，用于同层渲染的NativeImage的surfaceId。

详见[NativeEmbedDataInfo](../arkts-components/arkts-arkweb-web-nativeembeddatainfo-i.md)。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerSurfaceInfo-id: string--><!--Device-NativeMediaPlayerSurfaceInfo-id: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## rect

```TypeScript
rect: RectEvent
```

surface的位置信息。

**类型：** RectEvent

**起始版本：** 12

<!--Device-NativeMediaPlayerSurfaceInfo-rect: RectEvent--><!--Device-NativeMediaPlayerSurfaceInfo-rect: RectEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

