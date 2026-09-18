# UploadConfig

Describes the configuration of an upload task.

**Since:** 6

**System capability:** SystemCapability.MiscServices.Upload

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## begins

```TypeScript
begins?: number
```

File start point to read when the upload task begins, in bytes. The default value is **0**. The value is a closed interval, indicating that the file is read from the beginning.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.MiscServices.Upload

## data

```TypeScript
data: Array<RequestData>
```

Form data in the request body.

**Type:** Array&lt;[RequestData](arkts-basicservices-request-requestdata-i.md)&gt;

**Since:** 6

**System capability:** SystemCapability.MiscServices.Upload

## ends

```TypeScript
ends?: number
```

File end point to read when the upload task ends, in bytes. The default value is **-1**. The value is a closed interval, indicating that the file is read till the end.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.MiscServices.Upload

## files

```TypeScript
files: Array<File>
```

List of files to upload. The files are submitted in multipart/form-data format.

**Type:** Array&lt;[File](arkts-basicservices-request-file-i.md)&gt;

**Since:** 6

**System capability:** SystemCapability.MiscServices.Upload

## header

```TypeScript
header: Object
```

HTTP or HTTPS header added to an upload request.

**Type:** Object

**Since:** 6

**System capability:** SystemCapability.MiscServices.Upload

## index

```TypeScript
index?: number
```

Path index of the task. The default value is **0**.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.MiscServices.Upload

## method

```TypeScript
method: string
```

HTTP request method. The value can be **POST** or **PUT**. The default value is **POST**. Use **POST** to add resources and **PUT** to modify resources.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.MiscServices.Upload

## url

```TypeScript
url: string
```

Resource URL. From API version 6 to 14, the value contains a maximum of 2048 characters; since API version 15, the value contains a maximum of 8192 characters. [Intercepting HTTP](../../../basic-services/request/app-file-upload-download.md#intercepting-http) is supported.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.MiscServices.Upload
