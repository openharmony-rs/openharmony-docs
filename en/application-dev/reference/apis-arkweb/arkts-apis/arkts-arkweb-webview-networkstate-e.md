# NetworkState

Enumerates the network statuses of the player.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## EMPTY

```TypeScript
EMPTY = 0
```

The player has not started downloading data.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## IDLE

```TypeScript
IDLE = 1
```

The player's network activity is idle. This could mean that the download of a media segment is complete, and the player is waiting to start downloading the next segment.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## LOADING

```TypeScript
LOADING = 2
```

The player is downloading media data.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## NETWORK_ERROR

```TypeScript
NETWORK_ERROR = 3
```

A network error occurs.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
