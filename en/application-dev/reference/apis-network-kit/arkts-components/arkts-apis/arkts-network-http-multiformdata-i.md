# MultiFormData

```TypeScript
export interface MultiFormData
```

Defines the type of multi-form data.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## contentType

```TypeScript
contentType: string
```

Data type, for example, **text/plain**, **image/png**, **image/jpeg**, **audio/mpeg**, or **video/mp4**.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## data

```TypeScript
data?: string | Object | ArrayBuffer
```

Form data content.

**Type:** string &#124; Object &#124; ArrayBuffer

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## filePath

```TypeScript
filePath?: string
```

File path of the form data. If **data** is not specified, **filePath** must be set.

**Note:**  The file format supported by the file management module must be passed. You can call [access](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-access-f.md) to check whether the file exists and is accessible.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## name

```TypeScript
name: string
```

Data name.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## remoteFileName

```TypeScript
remoteFileName?: string
```

Name of the file uploaded to the server.

**Note:**  If this field is specified, the **filename** field is added to the request header, indicating the name of the file uploaded to the server.

(1) If the data to be uploaded is a file and the file content is specified via the **data** field, the **remoteFileName** field usually needs to be set to specify the name of the file to be uploaded to the server (the actual result depends on the server). If the file path is specified via the **filePath** field, the **filename** field will be automatically added to the request header. Its default value is the file name in the **filePath** field. If a different name is required, it can also be changed via this field.

(2) When the data to be uploaded is in binary format, the **remoteFileName** field must be set.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack
