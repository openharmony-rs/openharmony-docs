# FetchOptions

Defines the retrieval options.

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## fetchColumns

```TypeScript
fetchColumns: Array<string>
```

Names of the columns specified for query.

If this parameter is left blank for photos, photos are fetched by **'uri'**, **'media_type'**, **'subtype'**, and **'display_name'** by default. An error will be thrown if [get](arkts-medialibrary-photoaccesshelper-photoasset-i.md#get) is used to obtain other attributes of this object.

Example: **fetchColumns: ['uri', 'title']**.

If this parameter is left blank for albums, albums are fetched by **'uri'** and **'album_name'** by default.

**Type:** Array&lt;string&gt;

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## predicates

```TypeScript
predicates: dataSharePredicates.DataSharePredicates
```

Predicates that specify the fetch criteria.

**Type:** [dataSharePredicates.DataSharePredicates](../../apis-arkdata/arkts-apis/arkts-arkdata-datasharepredicates-datasharepredicates-c.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
