# Types
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

> **说明：**
>
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## MemberType

type MemberType = number | string | boolean

PhotoAsset的成员类型。

成员类型为下表类型的并集。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

| 类型 | 说明 |
| ---- | ---- |
| number | 表示值类型为数字，可取任意值。 |
| string | 表示值类型为字符，可取任意值。|
| boolean | 表示值类型为布尔类型。 |

## PhotoAssetParams<sup>21+</sup>

type PhotoAssetParams = Record\<string, MemberType\>[]

文件属性名称及其值的Record类型数组。

**系统能力**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| 类型 | 说明 |
| ---- | ---- |
| Record\<string, [MemberType](#membertype)\>[] | 文件属性名称及其值的Record类型数组。 |

