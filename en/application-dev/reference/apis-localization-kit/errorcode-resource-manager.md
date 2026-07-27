# Resource Manager Error Codes

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=cc8fe8b0f1b2859346994908b98ebf9b3df1ff9d translatedAt=2026-07-17T00:23:45.807Z pushedAt=2026-07-17T02:59:08.410Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 9001001 Invalid Resource ID

**Error Message**

Invalid resource ID.

**Description**

Invalid resource ID.

**Possible Causes**

1. The passed resource ID is invalid, such as `-1`.

2. The passed resource ID does not exist in the current HAP/HSP.

**Solution**

1. Check for any of the following cases: [HAR with obfuscation enabled](../../quick-start/har-package.md#obfuscation-configuration), intermediate-code HAR, bytecode HAR, and cross-HAP/HSP. In these four cases, the resource ID obtained through `$r('app.xxx.xxx').id` is `-1`. You are advised to use methods such as [getStringByName()](js-apis-resource-manager.md#getstringbyname9) to obtain resources by name.

2. Check whether the passed resource ID exists in the HAP/HSP. You can use the `dump` command of the [restool tool](../../tools/restool.md) to output the resource information of the HAP/HSP, and then search for the passed resource ID in the output.

## 9001002 Matching Resource Not Found Based on the Current Resource ID

**Error Message**

No matching resource is found based on the resource ID.

**Description**

No matching resource is found based on the current resource ID.

**Possible Causes**

1. The passed resource ID is incorrect.

2. The resource type corresponding to the passed resource ID does not match the currently called API. For example, if you want to obtain a string resource and call the `getStringSync` API, but the passed resource ID is `$r('app.integer.xxx').id`, the types do not match.

3. Resource reference resolution failed. The current resource references a non-existent resource.

**Solution**

1. Ensure that the passed resource ID meets expectations.

2. Ensure that the resource type corresponding to the passed resource ID matches the called API type.

3. Ensure that the resource corresponding to the passed resource ID references an existing resource.

## 9001003 Invalid Resource Name

**Error Message**

Invalid resource name.

**Description**

Invalid resource name.

**Possible Causes**

The passed resource name does not exist in the current HAP/HSP.

**Solution**

Check whether the passed resource name exists in the HAP/HSP. You can use the `dump` command of the [restool tool](../../tools/restool.md) to output the resource information of the HAP/HSP, and then search for the passed resource name in the output.

## 9001004 Matching Resource Not Found Based on the Passed Resource Name

**Error Message**

No matching resource is found based on the resource name.

**Description**

No matching resource is found based on the passed resource name.

**Possible Causes**

1. The resource name is incorrect.

2. The resource type corresponding to the resource name does not match the currently called API. For example, if you want to obtain a string resource and call the getStringByName API, but the specified resource name is the name of an integer type resource, the types do not match.

3. Resource reference resolution failed. The current resource references a non-existent resource.

**Solution**

1. Ensure that the passed resource name meets expectations.

2. Ensure that the resource type corresponding to the passed resource name matches the called API type.

3. Ensure that the resource corresponding to the passed resource name references an existing resource.

## 9001005 Invalid Relative Path

**Error Message**

Invalid relative path.

**Description**

Invalid relative path.

**Possible Causes**

The passed `rawfile` relative path is incorrect and does not match the actual relative path of the `rawfile` resource.

**Solution**

Ensure that the passed `rawfile` relative path meets expectations.

## 9001006 Circular Reference in Resources

**Error Message**

The resource is referenced cyclically.

**Description**

A circular reference exists in the resources.

**Possible Causes**

A circular reference exists in the resources, causing the number of reference resolutions to exceed 20.

**Solution**

Ensure that no circular reference exists when referencing other resources using methods such as `$string:xxx` and `$integer:xxx`.

## 9001007 Failed to Format the Resource Obtained Based on the Current ID

**Error Message**

Failed to format the resource obtained based on the resource ID.

**Description**

Failed to format the resource obtained based on the current ID.

**Possible Causes**

1. The type of the formatting parameter is not within the supported range.

2. The number of formatting parameters is inconsistent with the number of placeholders.

3. The type of the formatting parameter does not match the placeholder type.

**Solution**

1. Ensure that the type of the formatting parameter is within the supported range.

2. Ensure that the number of formatting parameters is consistent with the number of placeholders.

3. Ensure that the type of the formatting parameter is consistent with the placeholder type.

## 9001008 Failed to Format the Resource Obtained Based on resName

**Error Message**

Failed to format the resource obtained based on the resource name.

**Description**

Failed to format the resource obtained based on the current name.

**Possible Causes**

1. The type of the formatting parameter is not within the supported range.

2. The number of formatting parameters is inconsistent with the number of placeholders.

3. The type of the formatting parameter does not match the placeholder type.

**Solution**

1. Ensure that the type of the formatting parameter is within the supported range.

2. Ensure that the number of formatting parameters is consistent with the number of placeholders.

3. Ensure that the type of the formatting parameter is consistent with the placeholder type.

## 9001009 Failed to Obtain the System Resource Management Object

**Error Message**

Failed to access the system resource.

**Description**

Failed to obtain the system resource management object.

**Possible Causes**

System resources are not loaded to the sandbox path of the application process.

**Solution**

Ensure that the [application sandbox directory](../../../application-dev/file-management/app-sandbox-directory.md) of the application process contains system resources.

## 9001010 Invalid Overlay Path

**Error Message**

Invalid overlay path.

**Description**

Invalid overlay path.

**Possible Causes**

1. The specified overlay path does not exist.

2. The current application does not have permission to access the passed overlay path. For example, the path is not under the current application's installation path or other accessible paths.

**Solution**

1. Ensure that the overlay path is correct.

2. Ensure that the [application sandbox directory](../../../application-dev/file-management/app-sandbox-directory.md) of the application process contains the passed overlay path.
<!--no_check-->