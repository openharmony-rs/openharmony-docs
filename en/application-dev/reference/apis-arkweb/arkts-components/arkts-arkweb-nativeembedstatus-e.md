# NativeEmbedStatus

Enumerates the lifecycles of the same-layer tag. When a same-layer tag exists on the loaded page, **CREATE** is triggered. When a same-layer tag is moved or is enlarged, **UPDATE** is triggered. When the page exits, **DESTROY** is triggered.

**Since:** 11

**System capability:** SystemCapability.Web.Webview.Core

## CREATE

```TypeScript
CREATE = 0
```

The same-layer tag is created.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## UPDATE

```TypeScript
UPDATE = 1
```

The same-layer tag is updated.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## DESTROY

```TypeScript
DESTROY = 2
```

The same-layer tag is destroyed.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## ENTER_BFCACHE

```TypeScript
ENTER_BFCACHE = 3
```

The same-layer tag enters BFCache.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## LEAVE_BFCACHE

```TypeScript
LEAVE_BFCACHE = 4
```

The same-layer tag leaves BFCache.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
