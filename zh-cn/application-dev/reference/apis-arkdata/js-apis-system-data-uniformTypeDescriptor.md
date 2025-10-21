# @ohos.data.uniformTypeDescriptor (标准化数据定义与描述)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

本模块对标准化数据类型进行了抽象定义与描述。

> **说明：**
>
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import { uniformTypeDescriptor } from '@kit.ArkData';
```

## uniformTypeDescriptor.registerTypeDescriptors<sup>22+</sup>

registerTypeDescriptors(typeDescriptors: Array<TypeDescriptor>): Promise<void>

注册标准化数据类型描述符。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名  | 类型 | 必填  | 说明                    |
| -----  | ------  | ----  | ----------------------- |
| typeDescriptors    | Array<TypeDescriptor>  | 是    |要注册的标准化数据类型描述符列表。   |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| Promise\<void> | 无。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| **错误码ID** | **错误信息**                                |
| ------------ | ------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |
| 402          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |
| 20400002       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |
| 20400003       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.  |


**示例：**

```ts
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let typeId = new uniformTypeDescriptor.TypeDescriptor();
    uniformTypeDescriptor.registerTypeDescriptors([typeId]);
} catch(e) {
    let error: BusinessError = e as BusinessError;
    console.error(`registerTypeDescriptors throws an exception. code is ${error.code}, message is ${error.message} `);
}
```
