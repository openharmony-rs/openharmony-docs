# SearchPlayKaraokeItem

```TypeScript
interface SearchPlayKaraokeItem
```

The definition of SearchPlayKaraokeItem.

**Since:** 26.2.0

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## Modules to Import

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## entityId

```TypeScript
entityId: string
```

The unique identifier of the media resource.

**Type:** string

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## entityName

```TypeScript
entityName?: string
```

The name of the audio. When this parameter is left blank, the application searches for audio only based on entityId.

**Type:** string

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate
