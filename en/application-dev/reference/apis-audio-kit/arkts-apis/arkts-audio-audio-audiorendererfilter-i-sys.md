# AudioRendererFilter (System API)

```TypeScript
interface AudioRendererFilter
```

Describes audio renderer filter.

**Since:** 9

<!--Device-audio-interface AudioRendererFilter--><!--Device-audio-interface AudioRendererFilter-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## blockFirstOverrode

```TypeScript
blockFirstOverrode?: boolean
```

Keeps the first device selection not cleared. Default value: false.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioRendererFilter-blockFirstOverrode?: boolean--><!--Device-AudioRendererFilter-blockFirstOverrode?: boolean-End-->

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.

## rendererId

```TypeScript
rendererId?: number
```

AudioRenderer id.

**Type:** number

**Since:** 9

<!--Device-AudioRendererFilter-rendererId?: int--><!--Device-AudioRendererFilter-rendererId?: int-End-->

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.

## rendererInfo

```TypeScript
rendererInfo?: AudioRendererInfo
```

Renderer information.

**Type:** [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md)

**Since:** 9

<!--Device-AudioRendererFilter-rendererInfo?: AudioRendererInfo--><!--Device-AudioRendererFilter-rendererInfo?: AudioRendererInfo-End-->

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.

## uid

```TypeScript
uid?: number
```

Application uid.

**Type:** number

**Since:** 9

<!--Device-AudioRendererFilter-uid?: int--><!--Device-AudioRendererFilter-uid?: int-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.
