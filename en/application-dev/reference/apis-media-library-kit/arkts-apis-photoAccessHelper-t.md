# Types
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## MemberType

type MemberType = number | string | boolean

Defines the types of the PhotoAsset members.

The member types are the union of the types listed in the following table.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Type| Description|
| ---- | ---- |
| number | The member value is any number.|
| string | The member value is any string.|
| boolean | The member value is true or false.|

## PhotoAssetParams<sup>21+</sup>

type PhotoAssetParams = Record\<string, MemberType\>[]

Defines the array of record types that map file property names to their values.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Type| Description|
| ---- | ---- |
| Record\<string, [MemberType](#membertype)\>[] | Array of record types that map file property names to their values.|
