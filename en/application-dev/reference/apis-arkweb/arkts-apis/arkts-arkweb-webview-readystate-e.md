# ReadyState

Enumerates the cache states of the player.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## HAVE_NOTHING

```TypeScript
HAVE_NOTHING = 0
```

There is no data cached.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## HAVE_METADATA

```TypeScript
HAVE_METADATA = 1
```

Only media metadata is cached.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## HAVE_CURRENT_DATA

```TypeScript
HAVE_CURRENT_DATA = 2
```

Data up to the current playback position is cached.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## HAVE_FUTURE_DATA

```TypeScript
HAVE_FUTURE_DATA = 3
```

The buffered duration exceeds the current playback progress, but stuttering may still occur.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## HAVE_ENOUGH_DATA

```TypeScript
HAVE_ENOUGH_DATA = 4
```

Sufficient data has been cached to ensure smooth playback.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
