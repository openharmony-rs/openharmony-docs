# Types
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Types模块定义了照片资产管理中使用的核心数据类型，包括成员类型（MemberType）、文件属性参数类型（PhotoAssetParams）和操作值类型（OperationValueType）。这些类型为开发者提供了灵活的类型定义，支持对照片资产进行属性读取、查询条件构建等操作，适用于需要在应用中处理照片资产元数据的场景。

> **说明：**
>
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## MemberType<sup>10+</sup>

type MemberType = number | string | boolean

表示PhotoAsset的成员类型。

成员类型为下表类型的并集。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

| 类型 | 说明 |
| ---- | ---- |
| number | 表示值类型为数字，可取任意值。 |
| string | 表示值类型为字符串，可取任意值。|
| boolean | 表示值类型为布尔类型。 |

## PhotoAssetParams<sup>21+</sup>

type PhotoAssetParams = Record\<string, MemberType\>[]

文件属性名称及其值的Record类型数组。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

| 类型 | 说明 |
| ---- | ---- |
| Record\<string, [MemberType](#membertype)\>[] | 文件属性名称及其值的Record类型数组。 |

## OperationValueType<sup>22+</sup>

type OperationValueType = number | string | boolean  

表示不同谓词需要匹配的值。谓词用于定义文件查询条件，例如等于、大于、包含等操作符。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

| 类型                    | 说明                          |
| ---------------------- | -------------------------------- |
| number    | 表示值类型为数字，可取任意值。 |
| string    | 表示值类型为字符串，可取任意值。 |
| boolean   | 表示值类型为布尔值。 |