# BackForwardCacheSupportedFeatures

This class is used to enable back forward cache supported features.

**起始版本：** 12

<!--Device-webview-class BackForwardCacheSupportedFeatures--><!--Device-webview-class BackForwardCacheSupportedFeatures-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## constructor

```TypeScript
constructor()
```

**起始版本：** 12

<!--Device-BackForwardCacheSupportedFeatures-constructor()--><!--Device-BackForwardCacheSupportedFeatures-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## mediaTakeOver

```TypeScript
mediaTakeOver: boolean
```

是否允许使用视频托管的页面进入前进后退缓存。

如果设置为允许，需要维护为视频元素创建的系统控件的生命周期，避免造成泄漏。

true：允许使用视频托管的页面进入前进后退缓存，false：不允许使用视频托管的页面进入前进后退缓存。

默认值：false。

**类型：** boolean

**起始版本：** 12

<!--Device-BackForwardCacheSupportedFeatures-mediaTakeOver: boolean--><!--Device-BackForwardCacheSupportedFeatures-mediaTakeOver: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## nativeEmbed

```TypeScript
nativeEmbed: boolean
```

是否允许使用同层渲染的页面进入前进后退缓存。

如果设置为允许，需要维护为同层渲染元素创建的系统控件的生命周期，避免造成泄漏。

true：允许使用同层渲染的页面进入前进后退缓存，false：不允许使用同层渲染的页面进入前进后退缓存。

默认值：false。

**类型：** boolean

**起始版本：** 12

<!--Device-BackForwardCacheSupportedFeatures-nativeEmbed: boolean--><!--Device-BackForwardCacheSupportedFeatures-nativeEmbed: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

