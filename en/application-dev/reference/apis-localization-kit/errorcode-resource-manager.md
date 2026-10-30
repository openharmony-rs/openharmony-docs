# Resource Manager Error Codes

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 9001001 Invalid Resource ID

**Error Message**

Invalid resource ID.

**Description**

Invalid resource ID.

**Possible Causes**

1. The input resource ID is invalid, for example, **-1**.
2. The input resource ID does not exist in the current HAP/HSP.

**Solution**

1. Check for any of the following cases: HAR with [obfuscation](../../quick-start/har-package.md#configuring-obfuscation) enabled, intermediate-code HAR, bytecode HAR, and cross-HAP/HSP. When the resource ID **-1** is obtained through **$r('app.xxx.xxx').id** in the following cases, you are advised to use APIs such as [getStringByName()](js-apis-resource-manager.md#getstringbyname9) to obtain resources by name.
2. Check whether the input resource ID exists in the HAP/HSP. You can refer to the dump command of the [restool tool](../../tools/restool.md) to output the HAP/HSP resource information, and then search for the input resource ID in the output results.

## 9001002 Matching Resource Not Found Based on the Specified Resource ID

**Error Message**

No matching resource is found based on the resource ID.

**Description**

No matching resource is found based on the specified resource ID.

**Possible Causes**

1. The passed resource ID is incorrect.
2. The resource type corresponding to the passed resource ID does not match the type of the currently called API. For example, if you want to obtain a string resource, the API called is **getStringSync**, but the passed resource ID is **$r('app.integer.xxx').id**. The two types do not match.
3. The resource reference fails to parse because the current resource references a resource that does not exist.

**Solution**

1. Check whether the passed resource ID is correct.
2. Check whether the resource type corresponding to the passed resource ID matches the type of the called API.
3. Check whether the resource corresponding to the passed resource ID references a resource that does not exist.

## 9001003 Invalid Resource Name

**Error Message**

Invalid resource name.

**Description**

The resource name is invalid.

**Possible Causes**

The input resource name does not exist in the current HAP/HSP.

**Solution**

Check whether the input resource name exists in the HAP/HSP. You can refer to the dump command of the [restool tool](../../tools/restool.md) to output the HAP/HSP resource information, and then search for the input resource name in the output results.

## 9001004 Matching Resource Not Found Based on the Specified Resource Name

**Error Message**

No matching resource is found based on the resource name.

**Description**

No matching resource is found based on the specified resource name.

**Possible Causes**

1. The specified resource name is incorrect.
2. The resource type corresponding to the specified resource name does not match the type of the currently called API. For example, if you want to obtain a string resource, the API called is **getStringByName**, but the specified resource name is the name of an integer resource. The two types do not match.
3. The resource reference fails to parse because the current resource references a resource that does not exist.

**Solution**

1. Check whether the passed resource name is correct.
2. Check whether the resource type corresponding to the passed resource name matches the type of the called API.
3. Check whether the resource corresponding to the passed resource name references a resource that does not exist.

## 9001005 Invalid Relative Path

**Error Message**

Invalid relative path.

**Description**

The relative path is invalid.

**Possible Causes**

The passed relative path of the **rawfile** resource is incorrect and is inconsistent with the actual relative path of the **rawfile** resource.

**Solution**

Check whether the passed relative path of the **rawfile** resource is correct.

## 9001006 Resource Referenced Cyclically

**Error Message**

The resource is referenced cyclically.

**Description**

The resource is referenced cyclically.

**Possible Causes**

The resource is referenced cyclically. As a result, the number of parsing times exceeds 20.

**Solution**

Check whether cyclic reference exists when other resources are referenced using methods such as **$string:xxx** and **$integer:xxx**.

## 9001007 Failed to Format the Resource Obtained Based on the Current ID

**Error Message**

Failed to format the resource obtained based on the resource ID.

**Description**

The resource obtained based on the current ID fails to be formatted.

**Possible Causes**

1. The type of the formatting parameter is not supported.
2. The number of formatting parameters is inconsistent with the number of placeholders.
3. The type of the formatting parameter does not match the placeholder type.

**Solution**

1. Check whether the type of the formatting parameter is supported.
2. Check whether the number of formatting parameters is consistent with the number of placeholders.
3. Check whether the type of the formatting parameter is consistent with the type of the placeholder.

## 9001008 Failed to Format the Resource Obtained Based on resName

**Error Message**

Failed to format the resource obtained based on the resource name.

**Description**

The resource obtained based on the current name fails to be formatted.

**Possible Causes**

1. The type of the formatting parameter is not supported.
2. The number of formatting parameters is inconsistent with the number of placeholders.
3. The type of the formatting parameter does not match the placeholder type.

**Solution**

1. Check whether the type of the formatting parameter is supported.
2. Check whether the number of formatting parameters is consistent with the number of placeholders.
3. Check whether the type of the formatting parameter is consistent with the type of the placeholder.

## 9001009 Failed to Obtain a Resource Manager Object

**Error Message**

Failed to access the system resource.

**Description**

A Resource Manager Object fails to be obtained.

**Possible Causes**

System resources are not loaded to the sandbox path of the application process.

**Solution**

Check whether the [app sandbox directory](../../../application-dev/file-management/app-sandbox-directory.md) of the application process contains system resources.

## 9001010 Invalid Overlay Path

**Error Message**

Invalid overlay path.

**Description**

The overlay path is invalid.

**Possible Causes**

1. The input overlay path does not exist.
2. The current app does not have the access permission on the input overlay path. For example, the path is not in the installation path of the current app or any other accessible path.

**Solution**

1. Check whether the overlay path is correct.
2. Check whether the [app sandbox directory](../../../application-dev/file-management/app-sandbox-directory.md) of the application process contains the input overlay path.
