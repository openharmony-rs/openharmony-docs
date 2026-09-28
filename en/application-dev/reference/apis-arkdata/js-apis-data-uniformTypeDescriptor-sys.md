# @ohos.data.uniformTypeDescriptor (Uniform Data Definition and Description) (System API)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=6c1e7e2e5d533038514aef8a59f6b9dd1cac085e translatedAt=2026-09-04T03:57:11.116Z pushedAt=2026-09-09T09:11:03.740Z -->

A uniform data type (UTD) is a specification used in the Unified Data Management Framework (UDMF) to identify and describe data types, supporting cross-application data exchange. This module provides capabilities to register and unregister UTDs.

**Features**
- Supports dynamic registration of custom UTDs.
- Supports batch unregistration of registered UTDs.
- Supports associating file extensions and MIME types with custom types.

**Use Cases**
- An application needs to define its own data types and share them with other applications.
- A unified type identifier is required for cross-application data exchange.
- Preset data types need to be extended to meet specific business requirements.

Uniform data type descriptions ensure that different applications can identify and process the same type of data. They resolve the issue of inconsistent type identifiers during data exchange between applications, improve interoperability of data exchange between applications, and reduce data format compatibility issues.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This page contains only the system APIs of this module. For details about other public APIs, see [@ohos.data.uniformTypeDescriptor (Uniform Data Type Definition and Description)](js-apis-data-uniformTypeDescriptor.md).
>
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { uniformTypeDescriptor } from '@kit.ArkData';
```

## uniformTypeDescriptor.registerTypeDescriptors<sup>22+</sup>

registerTypeDescriptors(typeDescriptors: Array\<TypeDescriptor>): Promise\<void>

Registers a group of uniform data types to the system. This API uses a promise to return the result. After successful registration, the uniform data types are managed by the system and can be shared and identified across other applications or devices through the UDMF framework.

**Paired call**
- After a type is registered by calling this API, the registered type occupies system resources. You are advised to call **unregisterTypeDescriptors()** to unregister the type in a timely manner when the application exits or the type is no longer used.

**Required permissions:** ohos.permission.MANAGE_DYNAMIC_UTD_TYPE

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Atomic service API**: This API can be used in atomic services since API version 22.

**System API**: This is a system API.

**Parameters**

| Name | Type| Mandatory | Description|
|--------|------|------|------|
| typeDescriptors | Array\<[TypeDescriptor](js-apis-data-uniformTypeDescriptor.md#typedescriptor11)> | Yes | List of uniform data type descriptors to register. **TypeDescriptor** is used to describe the attributes of a custom data type, including the type ID, belonging types, file name extensions, MIME types, and so on. The list cannot be empty, and the number of elements cannot exceed 50. The total number of uniform data type descriptors registered by a single application cannot exceed 200.<br>**TypeDescriptor format requirements**<br>1. typeId cannot be an empty string. Its length cannot exceed 127, and it can contain only letters, digits, hyphens (-), and periods (.).<br>2. The number of elements in **belongingToTypes** cannot exceed 50. Each element cannot be an empty string, and its length cannot exceed 127.<br>3. The length of each of description, **referenceURL**, and **iconFile** cannot exceed 255.<br>4. The number of elements in **filenameExtensions** cannot exceed 50. Each element cannot be an empty string, its length cannot exceed 127, and its first character must be a period (.).<br>5. The number of elements in **mimeTypes** cannot exceed 50. Each element cannot be an empty string, and its length cannot exceed 127.<br>**TypeDescriptor content requirements**<br>1. **typeId** must be unique and cannot duplicate the **typeId** of a registered type.<br>2. typeId must start with the bundle name of the current application.<br>3. The uniform data type IDs in **belongingToTypes** must be [preset data types](../../database/uniform-data-type-list.md) or the **typeIds** of other uniform data types registered in this registration.<br>4. No circular dependency can exist between uniform data types. |

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [UDMF Error Codes](errorcode-udmf.md).

| **ID**| **Error Message**                               |
| ------------ | ------------------------------------------- |
| 201          | Permission verification failed. The application does not have the permission required to call the API. |
| 202          | Permission denied, non-system app called the system api. |
| 20400002       | The format of one or more typeDescriptors are invalid. |
| 20400003       | The content of one or more typeDescriptors violate rules. |

**Example**:

```ts
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const typeDescriptor = new uniformTypeDescriptor.TypeDescriptor();
  typeDescriptor.typeId = 'com.example.myHap.image';
  typeDescriptor.belongingToTypes = ['general.image'];
  typeDescriptor.filenameExtensions = ['.myImage'];
  typeDescriptor.mimeTypes = ['application/myImage'];
  typeDescriptor.description = 'myHap defined image type';
  await uniformTypeDescriptor.registerTypeDescriptors([typeDescriptor]);
  console.info('Type descriptors registered successfully.');
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`registerTypeDescriptors throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

## uniformTypeDescriptor.unregisterTypeDescriptors<sup>22+</sup>

unregisterTypeDescriptors(typeIds: Array\<string>): Promise\<void>

Unregisters one or more uniform data types from the system. This API uses a promise to return the result. After unregistration, the data types are no longer recognized by the system, and data that depends on these data types may fail to be processed properly. Ensure that related data dependencies are cleared before unregistration.

**Paired call**
- Unregisters the uniform data types registered through **registerTypeDescriptors()**.
- After unregistration, the types can no longer be recognized and used by the system.

**Required permissions:** ohos.permission.MANAGE_DYNAMIC_UTD_TYPE

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Atomic service API**: This API can be used in atomic services since API version 22.

**System API**: This is a system API.

**Parameters**

| Name | Type| Mandatory | Description|
| -------- | ------ | ---- | ---- |
| typeIds | Array\<string> | Yes | List of **typeId**s to unregister. The list cannot be empty, and the number of elements cannot exceed 50. The length of each item cannot exceed 127.<br>**typeId constraints:**<br>1. The uniform data type corresponding to the **typeId** must have been registered in the system;<br>2. The **typeId** must start with the bundle name of the current application;<br>3. The uniform data type corresponding to the **typeId** must have been registered through the [registerTypeDescriptors](#uniformtypedescriptorregistertypedescriptors22) API. |

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [UDMF Error Codes](errorcode-udmf.md).

| **ID**| **Error Message**                               |
| ------------ | ------------------------------------------- |
| 201          | Permission verification failed. The application does not have the permission required to call the API. |
| 202          | Permission denied, non-system app called the system api. |
| 20400004       |  One or more typeIds are invalid or do not exist. |

**Example**:

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const typeIds = ['com.example.myHap.image'];
  await uniformTypeDescriptor.unregisterTypeDescriptors(typeIds);
  console.info('Type descriptors unregistered successfully.');
} catch (e) {
  const error: BusinessError = e as BusinessError;
  console.error(`unregisterTypeDescriptors throws an exception. code is ${error.code}, message is ${error.message}`);
}
```
