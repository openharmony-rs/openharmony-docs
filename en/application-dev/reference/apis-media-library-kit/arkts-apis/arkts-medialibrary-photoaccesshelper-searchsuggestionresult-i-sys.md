# SearchSuggestionResult (System API)

```TypeScript
interface SearchSuggestionResult
```

Search suggestion result.

**Since:** 26.0.0

<!--Device-photoAccessHelper-interface SearchSuggestionResult--><!--Device-photoAccessHelper-interface SearchSuggestionResult-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## count

```TypeScript
count: number
```

Number of photos in the scenario where a recommendation word is searched. The value range is all integers.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SearchSuggestionResult-count: int--><!--Device-SearchSuggestionResult-count: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## type

```TypeScript
type: SearchSuggestionType
```

Search Suggestion Type

**Type:** [SearchSuggestionType](arkts-medialibrary-photoaccesshelper-searchsuggestiontype-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SearchSuggestionResult-type: SearchSuggestionType--><!--Device-SearchSuggestionResult-type: SearchSuggestionType-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## value

```TypeScript
value: string
```

Search suggestion

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SearchSuggestionResult-value: string--><!--Device-SearchSuggestionResult-value: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
