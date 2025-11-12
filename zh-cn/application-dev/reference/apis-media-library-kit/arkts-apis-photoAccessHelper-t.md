# Types

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## MemberType

ArkTS-Dyn: type MemberType = number | string | boolean

ArkTS-Sta: type MemberType = int | long | double | string | boolean

PhotoAsset的成员类型。

成员类型为下表类型的并集。

**系统能力**：SystemCapability.FileManagement.PhotoAccessHelper.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

| 类型 | 说明 |
| ---- | ---- |
| ArkTS-Dyn: number<br>ArkTS-Sta: int \| long \| double | 表示值类型为数字，可取任意值。 |
| string | 表示值类型为字符，可取任意值。|
| boolean | 表示值类型为布尔类型。 |
