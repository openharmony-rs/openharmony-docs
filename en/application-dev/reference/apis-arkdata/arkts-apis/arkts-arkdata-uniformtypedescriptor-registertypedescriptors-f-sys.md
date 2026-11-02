# registerTypeDescriptors (System API)

## Modules to Import

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
```

## registerTypeDescriptors

```TypeScript
function registerTypeDescriptors(typeDescriptors: Array<TypeDescriptor>): Promise<void>
```

Registers a group of uniform data types to the system. This API uses a promise to return the result. After successful registration, the uniform data types are managed by the system and can be shared and identified across other applications or devices through the UDMF framework.

**Since:** 22

**Required permissions:** ohos.permission.MANAGE_DYNAMIC_UTD_TYPE

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-uniformTypeDescriptor-function registerTypeDescriptors(typeDescriptors: Array<TypeDescriptor>): Promise<void>--><!--Device-uniformTypeDescriptor-function registerTypeDescriptors(typeDescriptors: Array<TypeDescriptor>): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typeDescriptors | Array&lt;[TypeDescriptor](arkts-arkdata-uniformtypedescriptor-typedescriptor-c.md)&gt; | Yes | List of uniform data type descriptors to register. **TypeDescriptor** is used to describe the attributes of a custom data type, including the type ID, belonging types, file name extensions, MIME types, and so on. The list cannot be empty, and the number of elements cannot xceed 50. The total number of uniform data type descriptors registered by a single application cannot exceed 200. <br>**TypeDescriptor format requirements** <br>1. typeId cannot be an empty string. Its length cannot exceed 127, and it can contain only letters, digits, hyphens (-), and periods (.). <br>2. The number of elements in **belongingToTypes** cannot exceed 50. Each element cannot be an empty string, and its length cannot exceed 127. <br>3. The length of each of description, **referenceURL**, and **iconFile** cannot exceed 255. <br>4. The number of elements in **filenameExtensions** cannot exceed 50. Each element cannot be an empty string, its length cannot exceed 127, and its first character must be a period (.). <br>5. The number of elements in **mimeTypes** cannot exceed 50. Each element cannot be an empty string, and its length cannot exceed 127. <br>**TypeDescriptor content requirements** <br>1. **typeId** must be unique and cannot duplicate the **typeId** of a registered type. <br>2. typeId must start with the bundle name of the current application. <br>3. The uniform data type IDs in **belongingToTypes** must be [preset data types](../../../database/uniform-data-type-list.md) or the **typeIds** of other uniform data types registered in this registration. <br>4. No circular dependency can exist between uniform data types. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [20400002](../errorcode-udmf.md#20400002-invalid-utd-format) | The format of one or more typeDescriptors are invalid. |
| [20400003](../errorcode-udmf.md#20400003-invalid-utd-content) | The content of one or more typeDescriptors violate rules. |
