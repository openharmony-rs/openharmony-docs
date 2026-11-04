# Resource Manager Error Codes

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=a8446c9be4dbeea364560754c05cf5bc58bb15cf translatedAt=2026-11-03T13:40:28.605Z pushedAt=2026-11-04T08:47:59.733Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 9001001 Invalid Resource ID

**Error Message**

Invalid resource ID.

**Description**

Invalid resource ID.

**Possible Causes**

1. The passed resource ID is an invalid value, for example, `-1`.
2. The passed resource ID does not exist in the current HAP/HSP package.

**Solution**

1. Check whether the following scenarios apply: HAR modules with [Obfuscation Configuration](../../quick-start/har-package.md#configuring-obfuscation) enabled, intermediate HAR, bytecode HAR, and cross-HAP/HSP packages. In these four scenarios, the resource ID obtained through `$r('app.xxx.xxx').id` is `-1`. It is recommended that you use methods such as [getStringByName()](js-apis-resource-manager.md#getstringbyname9) to obtain resources by name.
2. Check whether the passed resource ID exists in the HAP/HSP package. You can use the dump command of the [restool tool](../../tools/restool.md) to output the resource information of the HAP/HSP package, and then search the output for the passed resource ID.

## 9001002 No Matching Resource Found

**Error Message**

No matching resource is found based on the resource ID.

**Description**

No matching resource found for the current resource ID.

**Possible Causes**

1. The passed resource ID is incorrect.
2. The resource type corresponding to the passed resource ID does not match the currently called API. For example, if you want to obtain a string resource, you call getStringSync, but the passed resource ID is `$r('app.integer.xxx').id`, whose type does not match.
3. Resource reference resolution failed. The current resource references a nonexistent resource.

**Solution**

1. Check whether the passed resource ID is as expected.
2. Check whether the resource type corresponding to the passed resource ID matches the type of the called API.
3. Check whether the resource corresponding to the passed resource ID references a nonexistent resource.

## 9001003 Invalid Resource Name

**Error Message**

Invalid resource name.

**Description**

Invalid resource name.

**Possible Causes**

The passed resource name does not exist in the current HAP/HSP package.

**Solution**

Check whether the passed resource name exists in the HAP/HSP package. You can use the dump command of the [restool tool](../../tools/restool.md) to output the resource information of the HAP/HSP, and then search the output for the passed resource name.

## 9001004 No Matching Resource Found for the Current Resource Name

**Error Message**

No matching resource is found based on the resource name.

**Description**

No matching resource found for the current resource name.

**Possible Causes**

1. The passed resource name is incorrect.
2. The resource type corresponding to the passed resource name does not match the currently called API. For example, to obtain a string resource, the API called is getStringByName, but the passed resource name is the name of an integer resource, so the two types do not match.
3. Resource reference resolution failed. The current resource references a nonexistent resource.

**Solution**

1. Check whether the passed resource name meets expectations.
2. Check whether the resource type corresponding to the passed resource name matches the type of the called API.
3. Check whether the resource corresponding to the passed resource name references a nonexistent resource.

## 9001005 Invalid Relative Path

**Error Message**

Invalid relative path.

**Description**

Invalid relative path.

**Possible Causes**

The passed rawfile relative path is incorrect and does not match the actual relative path of the rawfile resource.

**Solution**

Check whether the rawfile relative path passed in meets expectations.

## 9001006 Circular Reference

**Error Message**

The resource is referenced cyclically.

**Description**

A circular reference exists in the resource.

**Possible Causes**

A circular reference exists in the resource, causing the number of reference resolutions to exceed 20.

**Solution**

Check whether a circular reference exists when referencing other resources using `$string:xxx`, `$integer:xxx`, and similar methods.

## 9001007 Failed to Format the Resource Obtained Based on the ID

**Error Message**

Failed to format the resource obtained based on the resource ID.

**Description**

Failed to format the resource obtained based on the current ID.

**Possible Causes**

1. The type of the format parameter is not within the supported range.
2. The number of format parameters is inconsistent with the number of placeholders.
3. The type of the format parameter does not match the type of the placeholder.

**Solution**

1. Check whether the type of the format parameter is within the supported range.
2. Check whether the number of format parameters is consistent with the number of placeholders.
3. Check whether the type of the format parameter is consistent with the type of the placeholder.

## 9001008 Failed to Format the Resource Obtained Based on resName

**Error Message**

Failed to format the resource obtained based on the resource name.

**Description**

Failed to format the resource obtained based on the current name.

**Possible Causes**

1. The type of the format parameter is not within the supported range.
2. The number of format parameters does not match the number of placeholders.
3. The type of the format parameter does not match the type of the placeholder.

**Solution**

1. Check whether the type of the format parameter is within the supported range.
2. Check whether the number of format parameters matches the number of placeholders.
3. Check whether the type of the format parameter matches the type of the placeholder.

## 9001009 Failed to Obtain the System Resource Manager Object

**Error Message**

Failed to access the system resource.

**Description**

Failed to obtain the system Resource Manager object.

**Possible Causes**

System resources are not loaded to the sandbox path of the application process.

**Solution**

Check whether the [app sandbox directory](../../../application-dev/file-management/app-sandbox-directory.md) of the application process contains system resources.

## 9001010 Invalid Overlay Path

**Error Message**

Invalid overlay path.

**Description**

Invalid overlay path.

**Possible Causes**

1. The passed-in overlay path does not exist.
2. The current application does not have the permission to access the passed-in overlay path. For example, the path is not in the installation path of the current application or any other accessible path.

**Solution**

1. Check whether the overlay path is correct.
2. Check whether the [app sandbox directory](../../../application-dev/file-management/app-sandbox-directory.md) of the application process contains the passed-in overlay path.