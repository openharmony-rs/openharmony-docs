# NativeEmbedStatus

Defines the lifecycle of the same-layer tag. When the same-layer tag exists on the loaded page, CREATE is triggered. When the same-layer tag is moved or is enlarged, **UPDATE **is triggered. When the page exits, DESTROY is triggered.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum NativeEmbedStatus--><!--Device-unnamed-export declare enum NativeEmbedStatus-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CREATE

```TypeScript
CREATE = 0
```

The same-layer tag is created.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-NativeEmbedStatus-CREATE = 0--><!--Device-NativeEmbedStatus-CREATE = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## UPDATE

```TypeScript
UPDATE = 1
```

The same-layer tag is updated.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-NativeEmbedStatus-UPDATE = 1--><!--Device-NativeEmbedStatus-UPDATE = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## DESTROY

```TypeScript
DESTROY = 2
```

The same-layer tag is destroyed.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-NativeEmbedStatus-DESTROY = 2--><!--Device-NativeEmbedStatus-DESTROY = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ENTER_BFCACHE

```TypeScript
ENTER_BFCACHE = 3
```

The same-layer tag enters the BFCache.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-NativeEmbedStatus-ENTER_BFCACHE = 3--><!--Device-NativeEmbedStatus-ENTER_BFCACHE = 3-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## LEAVE_BFCACHE

```TypeScript
LEAVE_BFCACHE = 4
```

The same-layer tag leaves the BFCache.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-NativeEmbedStatus-LEAVE_BFCACHE = 4--><!--Device-NativeEmbedStatus-LEAVE_BFCACHE = 4-End-->

**系统能力：** SystemCapability.Web.Webview.Core

