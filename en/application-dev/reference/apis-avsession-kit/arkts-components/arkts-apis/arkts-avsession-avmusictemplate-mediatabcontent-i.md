# MediaTabContent

The definition of the tab page content.

@extends OperResult @interface MediaTabContent

**Inheritance/Implementation:** MediaTabContent extends [OperResult](arkts-avsession-avmusictemplate-operresult-i.md)

**Since:** 23

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## Modules to Import

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## compilations

```TypeScript
compilations: Compilation[]
```

Compilations content of the tab page.

**Type:** [Compilation](arkts-avsession-avmusictemplate-compilation-i.md)[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## tabId

```TypeScript
tabId: string
```

Tab id corresponding to the content.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate
