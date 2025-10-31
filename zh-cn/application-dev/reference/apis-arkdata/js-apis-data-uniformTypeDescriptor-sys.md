# @ohos.data.uniformTypeDescriptor (标准化数据定义与描述)(系统接口)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

本模块提供标准化数据类型的注册与注销能力。

> **说明：**
>
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import { uniformTypeDescriptor } from '@kit.ArkData';
```

## uniformTypeDescriptor.registerTypeDescriptors

registerTypeDescriptors(typeDescriptors: Array\<TypeDescriptor>): Promise\<void>

注册一组标准化数据类型到系统中。

**需要权限:** ohos.permission.MANAGE_DYNAMIC_UTD_TYPE

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名  | 类型 | 必填  | 说明                    |
| -----  | ------  | ----  | ----------------------- |
| typeDescriptors    | Array\<[TypeDescriptor](js-apis-data-uniformTypeDescriptor.md#TypeDescriptor11)>  | 是    |待注册的标准化数据类型描述符列表。不可为空。<br>[TypeDescriptor](js-apis-data-uniformTypeDescriptor.md#TypeDescriptor11)格式要求：<br>1. typeId不可为空，长度不超过127且仅包含字母、数字、中划线（-）和点号（.）；<br>2. belongingToTypes长度不超过50且每项非空、每项长度不超过 127；<br>3. description/referenceURL/iconFile每项长度不超过 255；<br>4. filenameExtensions长度不超过50且每项非空、每项长度不超过127且首字符为点号；<br>5. mimeTypes长度不超过50且每项非空、每项长度不超过127。<br>[TypeDescriptor](js-apis-data-uniformTypeDescriptor.md#TypeDescriptor11)内容要求：<br>1. typeId必须唯一，不能与已注册类型重复；<br>2. typeId前缀需与当前应用包名匹配；<br>3. belongingToTypes中的类型 ID 必须已存在；<br>4. 不能形成循环依赖。   |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| Promise\<void> | 异步操作返回的Promise对象，无具体返回值。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[统一数据管理框架错误码](errorcode-udmf.md)。

| **错误码ID** | **错误信息**                                |
| ------------ | ------------------------------------------- |
| 201          | Permission verification failed. The application does not have the permission required to call the API. |
| 202          | Permission verification failed. A non-system application calls a system API. |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |
| 20400002       |  The format of one or more type descriptors are invalid. |
| 20400003       | The content of one or more type descriptors violate rules. |

**示例：**

```ts
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let typeDescriptor = new uniformTypeDescriptor.TypeDescriptor();
    typeDescriptor.typeId = 'com.example.myHap.image';
    typeDescriptor.belongingToTypes = ['general.image'];
    typeDescriptor.filenameExtensions = ['.myImage'];
    typeDescriptor.mimeTypes = ['application/myImage'];
    typeDescriptor.description = 'myHap defined image type';
    await uniformTypeDescriptor.registerTypeDescriptors([typeDescriptor]);
    console.log('Type descriptors registered successfully.');
} catch(e) {
    let error: BusinessError = e as BusinessError;
    console.error(`registerTypeDescriptors throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

## uniformTypeDescriptor.unregisterTypeDescriptors

unregisterTypeDescriptors(typeIds: Array\<string>): Promise\<void>

根据给定的类型ID列表，从系统中注销一个或多个标准化数据类型描述符。

**需要权限:** ohos.permission.MANAGE_DYNAMIC_UTD_TYPE

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名  | 类型 | 必填  | 说明                    |
| -----  | ------  | ----  | ----------------------- |
| typeIds    | Array\<string>  | 是    |待注销的typeId列表。不可为空。要求：<br>1. typeId对应的标准化数据类型存在。<br>2. typeId的前缀与当前应用的包名匹配。<br>3. typeId对应的标准化数据类型是由接口[registerTypeDescriptors](js-apis-data-uniformTypeDescriptor-sys.md#registerTypeDescriptors)注册的。   |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| Promise\<void> | 异步操作返回的Promise对象，无具体返回值。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[统一数据管理框架错误码](errorcode-udmf.md)。

| **错误码ID** | **错误信息**                                |
| ------------ | ------------------------------------------- |
| 201          | Permission verification failed. The application does not have the permission required to call the API. |
| 202          | Permission verification failed. A non-system application calls a system API. |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |
| 20400004       |  One or more typeIds are invalid or do not exist. |

**示例：**

```ts
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    const typeIds = ['com.example.myHap.image'];
    await uniformTypeDescriptor.unregisterTypeDescriptors(typeIds);
    console.log('Type descriptors unregistered successfully.');
} catch (e) {
    const error: BusinessError = e as BusinessError;
    console.error(`unregisterTypeDescriptors throws an exception. code is ${error.code}, message is ${error.message}`);
}
```
