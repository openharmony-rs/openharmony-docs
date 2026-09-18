# AVSessionDescriptor

The description of the session

**Since:** 23

**System capability:** SystemCapability.Multimedia.AVSession.Manager

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## elementName

```TypeScript
elementName: ElementName
```

The elementName of the ability that created this session. See [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md) in bundle/elementName.d.ts

**Type:** [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md)

**Since:** 23

**System capability:** SystemCapability.Multimedia.AVSession.Manager

## isActive

```TypeScript
isActive: boolean
```

Session active state

**Type:** boolean

**Since:** 23

**System capability:** SystemCapability.Multimedia.AVSession.Manager

## isTopSession

```TypeScript
isTopSession: boolean
```

Is it the top priority session

**Type:** boolean

**Since:** 23

**System capability:** SystemCapability.Multimedia.AVSession.Manager

## sessionId

```TypeScript
sessionId: string
```

Unique ID of the session

**Type:** string

**Since:** 23

**System capability:** SystemCapability.Multimedia.AVSession.Manager

## sessionTag

```TypeScript
sessionTag: string
```

The session tag set by the application

**Type:** string

**Since:** 23

**System capability:** SystemCapability.Multimedia.AVSession.Manager

## type

```TypeScript
type: AVSessionType
```

Session type, currently supports audio or video

**Type:** [AVSessionType](arkts-avsession-avsession-avsessiontype-t.md)

**Since:** 23

**System capability:** SystemCapability.Multimedia.AVSession.Manager
