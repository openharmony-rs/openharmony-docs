# @ohos.data.uniformTypeDescriptor(Uniform Data Definition and Description)

The **uniformTypeDescriptor** module abstracts and defines uniform data types.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace uniformTypeDescriptor--><!--Device-unnamed-declare namespace uniformTypeDescriptor-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getTypeDescriptor](arkts-arkdata-uniformtypedescriptor-gettypedescriptor-f.md#gettypedescriptor-1) | Obtains the **TypeDescriptor** object based on the uniform data type ID. |
| [getUniformDataTypeByFilenameExtension](arkts-arkdata-uniformtypedescriptor-getuniformdatatypebyfilenameextension-f.md#getuniformdatatypebyfilenameextension-1) | Obtains the uniform data type ID based on the given file name extension and data type. If there are multiple uniform data type IDs matching the conditions, the first one is returned. |
| [getUniformDataTypeByMIMEType](arkts-arkdata-uniformtypedescriptor-getuniformdatatypebymimetype-f.md#getuniformdatatypebymimetype-1) | Obtains the uniform data type ID based on the given MIME type and data type. If there are multiple uniform data type IDs matching the conditions, the first one is returned. |
| [getUniformDataTypesByFilenameExtension](arkts-arkdata-uniformtypedescriptor-getuniformdatatypesbyfilenameextension-f.md#getuniformdatatypesbyfilenameextension-1) | Obtains the uniform data type IDs based on the given file name extension and data type. |
| [getUniformDataTypesByMIMEType](arkts-arkdata-uniformtypedescriptor-getuniformdatatypesbymimetype-f.md#getuniformdatatypesbymimetype-1) | Obtains the uniform data type IDs based on the given MIME type and data type. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [registerTypeDescriptors](arkts-arkdata-uniformtypedescriptor-registertypedescriptors-f-sys.md#registertypedescriptors-1) | Registers a group of uniform data types to the system. This API uses a promise to return the result. After successful registration, the uniform data types are managed by the system and can be shared and identified across other applications or devices through the UDMF framework. |
| [unregisterTypeDescriptors](arkts-arkdata-uniformtypedescriptor-unregistertypedescriptors-f-sys.md#unregistertypedescriptors-1) | Unregisters one or more uniform data types from the system. This API uses a promise to return the result. After unregistration, the data types are no longer recognized by the system, and data that depends on these data types may fail to be processed properly. Ensure that related data dependencies are cleared before unregistration. |
<!--DelEnd-->

### Classes

| Name | Description |
| --- | --- |
| [TypeDescriptor](arkts-arkdata-uniformtypedescriptor-typedescriptor-c.md) | Represents a class for defining a uniform data type. It provides properties and methods for describing a uniform data type and its relationship with other uniform data types. |

### Enums

| Name | Description |
| --- | --- |
| [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md) | Enumerates the uniform data types. Some data types are related. For example, the JPEG type belongs to the IMAGE type. For more preset data types, see [Preset UTD List]. |
