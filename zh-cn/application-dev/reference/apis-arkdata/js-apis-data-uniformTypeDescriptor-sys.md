# @ohos.data.uniformTypeDescriptor (标准化数据定义与描述)(系统接口)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

标准化数据类型是统一数据管理框架（UDMF）中用于标识和描述数据类型的规范，支持跨应用数据交换。本模块提供标准化数据类型的注册与注销能力。

功能特点：
- 支持动态注册自定义标准化数据类型
- 支持批量注销已注册的标准化数据类型
- 支持自定义类型的文件扩展名和MIME类型关联

使用场景：
- 应用需要定义自己的数据类型并与其他应用共享
- 跨应用数据交换时需要统一的类型标识
- 需要扩展预置数据类型以满足特定业务需求

解决的问题：
解决了应用间数据交换时类型标识不统一的问题，通过标准化数据类型描述，确保不同应用能够识别和处理相同类型的数据。

带来的收益：
提升了应用间数据交换的互操作性，降低数据格式兼容性问题的发生。

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.data.uniformTypeDescriptor (标准化数据定义与描述)](js-apis-data-uniformTypeDescriptor.md)。
>
> - 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { uniformTypeDescriptor } from '@kit.ArkData';
```

## uniformTypeDescriptor.registerTypeDescriptors<sup>22+</sup>

registerTypeDescriptors(typeDescriptors: Array\<TypeDescriptor>): Promise\<void>

注册一组标准化数据类型到系统中。使用Promise异步回调。注册成功后，标准化数据类型将被系统管理，可通过UDMF框架在其他应用或设备间共享和识别。

使用场景：
- 应用需要定义自己的数据类型标识，用于跨应用数据共享和拖拽场景。
- 需要扩展系统预置数据类型，支持自定义文件格式或MIME类型。
- 应用间需要统一识别和处理特定格式的数据。

配对调用：
- 与registerTypeDescriptors接口配合使用，用于注销已注册的标准化数据类型。
- 只能注销通过registerTypeDescriptors接口注册的类型。
- 注销后，该类型将无法再被系统识别和使用。

**需要权限：** ohos.permission.MANAGE_DYNAMIC_UTD_TYPE

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名  | 类型 | 必填  | 说明 |
|--------|------|------|------|
| typeDescriptors | Array\<[TypeDescriptor](js-apis-data-uniformTypeDescriptor.md#typedescriptor11)> | 是 | 待注册的标准化数据类型描述符列表。TypeDescriptor用于描述自定义数据类型的属性，包括类型标识、所属类型、文件扩展名、MIME类型等。列表不可为空，其中元素个数不超过50。单个应用注册的标准化数据类型描述符数量总计不超过200。<br>**TypeDescriptor格式要求：**<br>1.typeId不可为空字符串，长度范围为1-127字符，且仅包含字母、数字、中划线（-）和点号（.）。<br>2.belongingToTypes中元素个数不超过50。每项不可为空字符串，长度不超过127。<br>3.description/referenceURL/iconFile每项长度不超过255。<br>4.filenameExtensions中元素个数不超过50。每项不可为空字符串，长度不超过127且首字符必须为点号。<br>5.mimeTypes中元素个数不超过50。每项不可为空字符串，长度不超过127。<br>**TypeDescriptor内容要求：**<br>1.typeId必须唯一，不能与已注册类型的typeId重复。<br>2.typeId必须以当前应用的包名开头。<br>3.belongingToTypes中的标准化数据类型ID必须为[预置数据类型](../../database/uniform-data-type-list.md)或本次注册的其他标准化数据类型的typeId。<br>4.标准化数据类型之间不能存在循环依赖关系。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| Promise\<void> | Promise对象，无返回结果。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[统一数据管理框架（UDMF）错误码](errorcode-udmf.md)。

| **错误码ID** | **错误信息**                                |
| ------------ | ------------------------------------------- |
| 201          | Permission verification failed. The application does not have the permission required to call the API. |
| 202          | Permission denied, non-system app called the system api. |
| 20400002       | The format of one or more typeDescriptors are invalid. Check typeId length, characters, or belongingToTypes format. |
| 20400003       | The content of one or more typeDescriptors violate rules. Check typeId uniqueness, package name prefix, or dependency relationships. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    const typeDescriptor = new uniformTypeDescriptor.TypeDescriptor();
    typeDescriptor.typeId = 'com.example.myHap.image';
    typeDescriptor.belongingToTypes = ['general.image'];
    typeDescriptor.filenameExtensions = ['.myImage'];
    typeDescriptor.mimeTypes = ['application/myImage'];
    typeDescriptor.description = 'myHap defined image type';
    await uniformTypeDescriptor.registerTypeDescriptors([typeDescriptor]);
    console.info('Type descriptors registered successfully.');
} catch(e) {
    let error: BusinessError = e as BusinessError;
    console.error(`registerTypeDescriptors throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

## uniformTypeDescriptor.unregisterTypeDescriptors<sup>22+</sup>

unregisterTypeDescriptors(typeIds: Array\<string>): Promise\<void>

从系统中注销一个或多个标准化数据类型。使用Promise异步回调。注销后，该数据类型将不再被系统识别，依赖该数据类型的数据可能无法正常处理，请确保在注销前已清理相关数据依赖。

使用场景：*
- 应用卸载或功能下线时，清理已注册的自定义数据类型。
- 应用更新时，注销旧的不再使用的数据类型定义。
- 动态调整应用支持的数据类型范围。

配对调用：
- 调用registerTypeDescriptors注册类型后，应在不需要时调用unregisterTypeDescriptors注销。
- 注册的类型会占用系统资源，建议在应用退出或类型不再使用时及时注销。
- 与unregisterTypeDescriptors接口配合使用，实现类型的注册与注销。

**需要权限：** ohos.permission.MANAGE_DYNAMIC_UTD_TYPE

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名  | 类型 | 必填  | 说明 |
| -------- | ------ | ---- | ---- |
| typeIds | Array\<string> | 是 | 待注销的typeId列表。列表不可为空，其中元素个数不超过50。每项长度范围为1-127字符。<br>**typeId约束限制：**<br>1.typeId对应的标准化数据类型必须在系统中已注册；<br>2.typeId必须以当前应用的包名开头；<br>3.typeId对应的标准化数据类型必须已通过[registerTypeDescriptors](#uniformtypedescriptorregistertypedescriptors22)接口注册。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[统一数据管理框架（UDMF）错误码](errorcode-udmf.md)。

| **错误码ID** | **错误信息**                                |
| ------------ | ------------------------------------------- |
| 201          | Permission verification failed. The application does not have the permission required to call the API. |
| 202          | Permission denied, non-system app called the system api. |
| 20400004       | One or more typeIds are invalid or do not exist. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    const typeIds = ['com.example.myHap.image'];
    await uniformTypeDescriptor.unregisterTypeDescriptors(typeIds);
    console.info('Type descriptors unregistered successfully.');
} catch (e) {
    const error: BusinessError = e as BusinessError;
    console.error(`unregisterTypeDescriptors throws an exception. code is ${error.code}, message is ${error.message}`);
}
```
