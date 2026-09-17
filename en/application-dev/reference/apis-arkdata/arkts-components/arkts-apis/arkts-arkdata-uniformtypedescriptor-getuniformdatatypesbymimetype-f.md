# getUniformDataTypesByMIMEType

## Modules to Import

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
```

## getUniformDataTypesByMIMEType

```TypeScript
function getUniformDataTypesByMIMEType(mimeType: string, belongsTo?: string): Array<string>
```

Obtains the uniform data type IDs based on the given MIME type and data type.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mimeType | string | Yes | MIME type. |
| belongsTo | string | No | ID of the uniform data type, to which the data type to be obtained belongs. This parameter has no default value. If it is not specified, the [uniform data type ID] is queried based on the MIME name. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Uniform data type IDs that match the specified MIME type and **belongsTo** (if specified). If no match is found, the data types dynamically generated based on the rules specified by the input parameters are returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types; <br>3. Parameter verification failed. |

**Examples**

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let typeIds = uniformTypeDescriptor.getUniformDataTypesByMIMEType('text/plain', 'general.text');
  for (let typeId of typeIds) {
    console.info(`typeId is ${typeId}`);
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`getUniformDataTypesByMIMEType throws an exception. code is ${error.code}, message is ${error.message} `);
}

// If no preset data type is found for "image/myimage" and "general.image", return the dynamic type list generated based on the input parameters.
try {
  let flexTypeIds = uniformTypeDescriptor.getUniformDataTypesByMIMEType('image/myimage', 'general.image');
  for (let flexTypeId of flexTypeIds) {
    console.info(`typeId is flex type, flex typeId is ${flexTypeId}`);
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`getUniformDataTypesByMIMEType throws an exception. code is ${error.code}, message is ${error.message} `);
}
```
