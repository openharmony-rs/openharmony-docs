# BackForwardCacheOptions

BackForwardCacheOptions是ArkWeb框架中用于配置Web组件前进后退缓存（BFCache）行为的参数类。BFCache是一种页面缓存机制，当用户在浏览历史中前进或后退时，可将页面完整快照（包括 JavaScript状态）缓存起来，实现瞬时加载效果，显著提升用户体验。通过BackForwardCacheOptions，开发者可以控制每个Web组件允许缓存的最大页面个数以及页面在缓存中的最长停留时间。

**起始版本：** 12

<!--Device-webview-class BackForwardCacheOptions--><!--Device-webview-class BackForwardCacheOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## constructor

```TypeScript
constructor()
```

BackForwardCacheOptions的构造函数。

**起始版本：** 12

<!--Device-BackForwardCacheOptions-constructor()--><!--Device-BackForwardCacheOptions-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## size

```TypeScript
size: number
```

设置每个Web组件允许缓存的最大页面个数。 默认为1，最大可设置为50。 设置为0或负数时，前进后退缓存功能不生效。 Web组件会根据内存压力对缓存进行回收。

**类型：** number

**起始版本：** 12

<!--Device-BackForwardCacheOptions-size: number--><!--Device-BackForwardCacheOptions-size: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## timeToLive

```TypeScript
timeToLive: number
```

设置每个Web组件允许页面在前进后退缓存中停留的时间。 设置为0或负数时，前进后退缓存功能不生效。 默认值：600。

**类型：** number

**起始版本：** 12

<!--Device-BackForwardCacheOptions-timeToLive: number--><!--Device-BackForwardCacheOptions-timeToLive: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

