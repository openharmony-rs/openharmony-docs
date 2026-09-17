# @ohos.file.hash(File Hash Processing)

The **FileHash** module implements hash processing on files.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { hash } from '@kit.CoreFileKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createHash](arkts-corefile-hash-createhash-f.md) | Creates a **HashStream** instance, which can be used to generate a message digest (a hash value) using the given algorithm. |
| [hash](arkts-corefile-hash-f.md) | Calculates a hash value for a file. This API uses a promise to return the result. |
| [hash](arkts-corefile-hash-f.md) | Calculates a hash value for a file. This API uses an asynchronous callback to return the result. |

### Classes

| Name | Description |
| --- | --- |
| [HashStream](arkts-corefile-hash-hashstream-c.md) | The **HashStream** class is a utility for creating a message digest of data. You can use [createHash](../../../reference/apis-core-file-kit/js-apis-file-hash.md#hashcreatehash12) to create a **HashStream** instance. |
