# File

Describes the list of files in [UploadConfig](arkts-basicservices-request-uploadconfig-i.md).

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## filename

```TypeScript
filename: string
```

File name in the header when **multipart** is used.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download

## name

```TypeScript
name: string
```

Name of a form item when **multipart** is used. The default value is **file**.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download

## type

```TypeScript
type: string
```

Type of the file content. By default, the type is obtained based on the extension of the file name or URI.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download

## uri

```TypeScript
uri: string
```

Local path for storing files.

Only **internal://cache/** is supported, that is, **context.cacheDir** of the caller (namely, cache directory of the input **context**).

Example: **internal://cache/path/to/file.txt**.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download
