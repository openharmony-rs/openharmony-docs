# UDMF Error Codes
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 20400001 Settings Already Exist

**Error Message**

Settings already exist. To reconfigure, remove the existing sharing options.

**Description**

The data to be set by **setAppShareOptions()** already exists.

**Possible Causes**

This error code is reported when [setAppShareOptions](js-apis-data-unifiedDataChannel.md#unifieddatachannelsetappshareoptions14) is called repeatedly to set **ShareOptions** of the drag-and-drop channel data.

**Solution**

Call [removeAppShareOptions](js-apis-data-unifiedDataChannel.md#unifieddatachannelremoveappshareoptions14) to clear the **ShareOptions** of the current drag-and-drop channel data, and then call [setAppShareOptions](js-apis-data-unifiedDataChannel.md#unifieddatachannelsetappshareoptions14) to set **ShareOptions**.

<!--Del-->
## 20400002 Invalid UTD Format

**Error Message**

The format of one or more type descriptors are invalid.

**Description**

This error code is reported when the UTD format is invalid.

**Possible Causes**

When [registerTypeDescriptors](js-apis-data-uniformTypeDescriptor-sys.md#uniformtypedescriptorregistertypedescriptors22) is called, the format of the input UTDs is invalid. The possible causes are as follows:

1. The UTD list is empty, the number of elements in the list exceeds 50, or the total number of UTDs registered by the current application exceeds 200.

2. The format of any UTD is incorrect. Examples:

    - **typeId** is an empty string, contains more than 127 characters, or contains non-alphabetic characters, digits, hyphens (-), and periods (.).
    
    - **belongingToTypes** is an empty list, the number of elements in the list exceeds 50, the list contains empty strings, or any element contains more than 127 characters.

    - **description**, **referenceURL**, or **iconFile** contains more than 255 characters.

    - **filenameExtensions** contains more than 50 elements, the list contains empty strings, any element contains more than 127 characters, or the first character of an element is not a period (.).

    - **mimeTypes** contains more than 50 elements, the list contains empty strings, or any element contains more than 127 characters.

**Solution**

Check the format of input UTDs and modify the invalid format by referring to the preceding possible causes.

## 20400003 Invalid UTD Content

**Error Message**

The content of one or more type descriptors are invalid.

**Description**

This error code is reported when the content of UTDs is invalid.

**Possible Causes**

When [registerTypeDescriptors](js-apis-data-uniformTypeDescriptor-sys.md#uniformtypedescriptorregistertypedescriptors22) called, the content of input UTDs is invalid. The possible causes are as follows:

1. **typeId** of any UTD is the same as the registered type ID.

2. **typeId** of any UTD does not start with the bundle name of the current application.

3. **belongingToTypes** contains **typeId** that does not belong to the [prebuilt UTDs](../../database/uniform-data-type-list.md) or other UTDs registered this time.

4. Cyclic dependency exists between UTDs, and the **belongingToTypes** content is invalid.

**Solution**

Check the content of input UTDs and modify the invalid content by referring to the preceding possible causes.

## 20400004 Invalid UTD IDs

**Error Message**
 
One or more typeIds are invalid or do not exist.

**Description**

This error code is reported when the UTD IDs to be unregistered contains invalid IDs.

**Possible Causes**

When [unregisterTypeDescriptors](js-apis-data-uniformTypeDescriptor-sys.md#uniformtypedescriptorunregistertypedescriptors22) is called, the input UTD IDs are invalid. The possible causes are as follows:

1. The UTD ID list is empty or the number of elements in the list exceeds 50.

2. Any UTD ID is invalid. Examples:

    - The UTD corresponding to the ID is not registered with the system.

    - The UTD ID does not start with the bundle name of the current application.

    - The UTD corresponding to the ID is not registered through the [registerTypeDescriptors](js-apis-data-uniformTypeDescriptor-sys.md#uniformtypedescriptorregistertypedescriptors22) API.

**Solution**

Check the UTD IDs and modify the invalid ID by referring to the preceding possible causes.
<!--DelEnd-->
