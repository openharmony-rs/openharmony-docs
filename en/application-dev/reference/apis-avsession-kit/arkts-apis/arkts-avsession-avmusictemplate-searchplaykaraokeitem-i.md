# SearchPlayKaraokeItem

```TypeScript
interface SearchPlayKaraokeItem
```

The definition of SearchPlayKaraokeItem.

**Since:** 26.0.1

<!--Device-avMusicTemplate-interface SearchPlayKaraokeItem--><!--Device-avMusicTemplate-interface SearchPlayKaraokeItem-End-->

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

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SearchPlayKaraokeItem-entityId: string--><!--Device-SearchPlayKaraokeItem-entityId: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## entityName

```TypeScript
entityName?: string
```

The name of the audio. When this parameter is left blank, the application searches for audio only based on entityId.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SearchPlayKaraokeItem-entityName?: string--><!--Device-SearchPlayKaraokeItem-entityName?: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate
