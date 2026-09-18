# FileSpec

Provides the file information of a table item.

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## contentType

```TypeScript
contentType?: string
```

Content type of the file. The default value is the file name extension. This option is filled in the **Content-Type** field specified in the HTTP form.

**Type:** string

**Since:** 18

**System capability:** SystemCapability.Request.FileTransferAgent

## extras

```TypeScript
extras?: object
```

Additional information. This parameter is not included in HTTP requests. The default value is empty.

**Type:** object

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## filename

```TypeScript
filename?: string
```

File name. The default value is obtained from the file path.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## mimeType

```TypeScript
mimeType?: string
```

MIME type of the file, which is obtained from the file name. The default value is the file name extension.

This API is deprecated since API version 18. You are advised to use **contentType** instead.

**Type:** string

**Since:** 10

**Deprecated since:** 18

**Substitutes:** [contentType](#contenttype)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## path

```TypeScript
path: string
```

File path.

- Relative path, which is in the cache directory of the caller.

Example: **./xxx/yyy/zzz.html** or **xxx/yyy/zzz.html**

- Internal protocol path, which can be **internal://** or its subdirectory. **internal** indicates the cache  
directory of the caller (that is, the input **context**), and **internal://cache** corresponds to **context.cacheDir**.

Example: **internal://cache/path/to/file.txt**

- Application sandbox directory. Only the **base** directory and its subdirectories are supported.

Example: **./data/storage/el1/base/path/to/file.txt**

- File protocol path, which must match the application bundle name. Only the **base** directory and its  
subdirectories are supported.

Example: **file://com.example.test/data/storage/el2/base/file.txt**

- Public files of users. Only upload tasks are supported.

Example: **file://media/Photo/path/to/file.img**. Only foreground tasks are supported.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

**Test API:** This API is used only in automated test scripts.
