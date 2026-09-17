# PressureLevel

Enumerates the memory pressure levels. When an application clears the cache occupied by the **Web** component, the **Web** kernel releases the cache based on the memory pressure level.

**Since:** 14

**System capability:** SystemCapability.Web.Webview.Core

## MEMORY_PRESSURE_LEVEL_MODERATE

```TypeScript
MEMORY_PRESSURE_LEVEL_MODERATE = 1
```

Moderate memory pressure level. At this level, the **Web** kernel attempts to release the cache that has low reallocation overhead and does not need to be used immediately.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Web.Webview.Core

## MEMORY_PRESSURE_LEVEL_CRITICAL

```TypeScript
MEMORY_PRESSURE_LEVEL_CRITICAL = 2
```

Critical memory pressure level. At this level, the **Web** kernel attempts to release all possible memory caches.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Web.Webview.Core
