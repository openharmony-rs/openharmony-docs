# CustomizeData
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

The CustomizeData module provides custom metadata.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> The APIs of this module are deprecated since API version 9. You are advised to use [Metadata](js-apis-bundleManager-metadata.md) instead.

## CustomizeData<sup>(deprecated)</sup>

This API is deprecated since API version 9. You are advised to use [Metadata](js-apis-bundleManager-metadata.md#metadata-1) instead.

**System capability**: SystemCapability.BundleManager.BundleFramework



| Name              | Type  | Read-Only| Optional| Description            |
| ------------------ | ------ | ---- | ---- | ---------------- |
| name               | string | No  | No  | Key that identifies a data element.|
| value              | string | No  | No  | Value of the data element.  |
| extra<sup>8+</sup> | string | No  | No  | Custom format of the data element. The value is an index to the resource that identifies the data.      |
