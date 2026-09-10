# CustomizeData
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1bd317f06f1afd85920306c4a4cf71333749080f translatedAt=2026-09-03T11:04:09.898Z pushedAt=2026-09-05T10:47:30.522Z -->

The CustomizeData module provides custom metadata.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with the superscript to indicate their earliest API version.
> 
> This module is no longer maintained since API version 9. You are advised to use [Metadata](js-apis-bundleManager-metadata.md) instead.

## CustomizeData<sup>(deprecated)</sup>

> **NOTE**
>
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use [Metadata](js-apis-bundleManager-metadata.md#metadata-1) instead.

**System capability**: SystemCapability.BundleManager.BundleFramework



| Name              | Type  | Read-Only| Optional| Description            |
| ------------------ | ------ | ---- | ---- | ---------------- |
| name               | string | No  | No  | Key that identifies a data element.|
| value              | string | No  | No  | Value of the data element.  |
| extra<sup>8+</sup> | string | No  | No  | Custom format of the data element. The value is an index to the resource that identifies the data.      |