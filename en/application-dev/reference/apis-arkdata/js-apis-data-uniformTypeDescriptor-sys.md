# @ohos.data.uniformTypeDescriptor (Uniform Data Definition and Description) (System API)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

This module provides capabilities to register and unregister UTDs.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.data.uniformTypeDescriptor (Uniform Data Definition and Description)](js-apis-data-uniformTypeDescriptor.md).

## Modules to Import

```ts
import { uniformTypeDescriptor } from '@kit.ArkData';
```

## uniformTypeDescriptor.registerTypeDescriptors<sup>22+</sup>

registerTypeDescriptors(typeDescriptors: Array\<TypeDescriptor>): Promise\<void>

Registers a group of UTDs with the system. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_DYNAMIC_UTD_TYPE

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Atomic service API**: This API can be used in atomic services since API version 22.

**System API**: This is a system API.

**Parameters**

| Name | Type| Mandatory | Description|
|--------|------|------|------|
| typeDescriptors | Array\<[TypeDescriptor](js-apis-data-uniformTypeDescriptor.md#typedescriptor11)> | Yes| List of UTDs to be registered. This list cannot be empty and contains no more than 50 elements. The total number of UTDs registered for a single application cannot exceed 200.<br>**Standard formats for TypeDescriptor**:<br>1. **typeId** cannot be an empty string and can contain a maximum of 127 characters, including only letters, digits, hyphens (-), and periods (.).<br>2. The number of elements in **belongingToTypes** cannot exceed 50. Each item cannot be an empty string and can contain a maximum of 127 characters.<br>3. The length of each **description**/**referenceURL**/**iconFile** cannot exceed 255 characters.<br>4. The number of elements in **filenameExtensions** cannot exceed 50. Each item cannot be an empty string and can contain a maximum of 127 characters. The first character must be a period (.).<br>5. The number of elements in **mimeTypes** cannot exceed 50. Each item cannot be an empty string and can contain a maximum of 127 characters.<br>**Content requirements for TypeDescriptor**:<br>1. **typeId** must be unique and cannot be the same as the registered type ID.<br>2. **typeId** must start with the bundle name of the current application.<br>3. The UTD IDs in **belongingToTypes** must belong to the [prebuilt UTDs](../../database/uniform-data-type-list.md) or other UTDs registered this time.<br>4. There is no cyclic dependency between UTDs.|

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
| 20400002       |  The format of one or more type descriptors are invalid. |
| 20400003       | The content of one or more type descriptors violate rules. |

**Example**:

```ts
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
} catch(e) {
    let error: BusinessError = e as BusinessError;
    console.error(`registerTypeDescriptors throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

## uniformTypeDescriptor.unregisterTypeDescriptors<sup>22+</sup>

unregisterTypeDescriptors(typeIds: Array\<string>): Promise\<void>

Unregisters one or more UTDs from the system. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_DYNAMIC_UTD_TYPE

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Atomic service API**: This API can be used in atomic services since API version 22.

**System API**: This is a system API.

**Parameters**

| Name | Type| Mandatory | Description|
| -------- | ------ | ---- | ---- |
| typeIds | Array\<string> | Yes| List of type IDs to be unregistered. This list cannot be empty and contains no more than 50 elements.<br>**Constraints on typeId**:<br>1. The UTD corresponding to the ID must have been registered with the system.<br>2. **typeId** must start with the bundle name of the current application.<br>3. The UTD corresponding to the ID must have been registered through the [registerTypeDescriptors](#uniformtypedescriptorregistertypedescriptors22) API.|

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
