# CastDisplayInfo

```TypeScript
interface CastDisplayInfo
```

Define the information for extended display screen.

**Since:** 12

<!--Device-avSession-interface CastDisplayInfo--><!--Device-avSession-interface CastDisplayInfo-End-->

**System capability:** SystemCapability.Multimedia.AVSession.ExtendedDisplayCast

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## height

```TypeScript
height: number
```

Display height, in pixels.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CastDisplayInfo-height: int--><!--Device-CastDisplayInfo-height: int-End-->

**System capability:** SystemCapability.Multimedia.AVSession.ExtendedDisplayCast

## id

```TypeScript
id: number
```

Display ID. The application can get more display information based on the same id from display interface.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CastDisplayInfo-id: long--><!--Device-CastDisplayInfo-id: long-End-->

**System capability:** SystemCapability.Multimedia.AVSession.ExtendedDisplayCast

## name

```TypeScript
name: string
```

Display name.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CastDisplayInfo-name: string--><!--Device-CastDisplayInfo-name: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.ExtendedDisplayCast

## state

```TypeScript
state: CastDisplayState
```

The state of display.

**Type:** [CastDisplayState](arkts-avsession-avsession-castdisplaystate-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CastDisplayInfo-state: CastDisplayState--><!--Device-CastDisplayInfo-state: CastDisplayState-End-->

**System capability:** SystemCapability.Multimedia.AVSession.ExtendedDisplayCast

## width

```TypeScript
width: number
```

Display width, in pixels.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CastDisplayInfo-width: int--><!--Device-CastDisplayInfo-width: int-End-->

**System capability:** SystemCapability.Multimedia.AVSession.ExtendedDisplayCast
