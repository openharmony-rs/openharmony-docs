# FetchOptions (System API)

Defines the options for fetching file attributes.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [FetchOptions](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchoptions-i.md)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userFileManager } from '@kit.CoreFileKit';
```

## fetchColumns

```TypeScript
fetchColumns: Array<string>
```

Options for fetching files based on the attributes in columns. If this parameter is left empty, files are fetched by URI, name, and type (the specific field names vary with the file asset or album object) by default. In addition, an error will be reported if [get](arkts-corefile-userfilemanager-userfilemanager-i-sys.md#getphotoassets) is called to obtain other attributes of this object. Example:

fetchColumns: ['uri', 'title']

**Type:** Array&lt;string&gt;

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [fetchColumns](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchoptions-i.md#fetchcolumns)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## predicates

```TypeScript
predicates: dataSharePredicates.DataSharePredicates
```

Predicates that specify the fetch criteria.

**Type:** [dataSharePredicates.DataSharePredicates](../../apis-arkdata/arkts-apis/arkts-arkdata-datasharepredicates-datasharepredicates-c.md)

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [predicates](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchoptions-i.md#predicates)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.
