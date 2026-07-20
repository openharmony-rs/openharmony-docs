# BackForwardCacheOptions

前进后退缓存相关设置对象，用来控制Web组件前进后退缓存相关选项。

**起始版本：** 12

<!--Device-webview-class BackForwardCacheOptions--><!--Device-webview-class BackForwardCacheOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

**起始版本：** 12

<!--Device-BackForwardCacheOptions-constructor()--><!--Device-BackForwardCacheOptions-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## size

```TypeScript
size: number
```

设置每个Web组件允许缓存的最大页面个数。

默认为1，最大可设置为50。

设置为0或负数时，前进后退缓存功能不生效。

Web会根据内存压力对缓存进行回收。

**类型：** number

**起始版本：** 12

<!--Device-BackForwardCacheOptions-size: number--><!--Device-BackForwardCacheOptions-size: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## timeToLive

```TypeScript
timeToLive: number
```

设置每个Web组件允许页面在前进后退缓存中停留的时间。

设置为0或负数时，前进后退缓存功能不生效。

单位：秒。默认值：600。

**类型：** number

**起始版本：** 12

<!--Device-BackForwardCacheOptions-timeToLive: number--><!--Device-BackForwardCacheOptions-timeToLive: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

