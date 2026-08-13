# PrefetchOptions

Defines the PrefetchOptions class.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-webview-class PrefetchOptions--><!--Device-webview-class PrefetchOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor for PrefetchOptions.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-PrefetchOptions-constructor()--><!--Device-PrefetchOptions-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ignoreCacheControlNoStore

```TypeScript
ignoreCacheControlNoStore: boolean
```

Set whether to ignore Cache-Control: no-store‌. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; This setting controls whether prefetch operations bypass the HTTP Cache-Control: no-store directive. Important‌: Default behavior (false) aligns with HTTP security standards. Overriding (true) requires explicit risk assessment for non-sensitive resources.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-PrefetchOptions-ignoreCacheControlNoStore: boolean--><!--Device-PrefetchOptions-ignoreCacheControlNoStore: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## minTimeBetweenPrefetchesMs

```TypeScript
minTimeBetweenPrefetchesMs: int
```

‌Set prefetch page interval limit. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:&lt;br&gt; Unit: ms. Default 500ms (ensures only one successful prefetch within 500ms). The interval throttles prefetch frequency to balance performance and resource usage.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-PrefetchOptions-minTimeBetweenPrefetchesMs: int--><!--Device-PrefetchOptions-minTimeBetweenPrefetchesMs: int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

