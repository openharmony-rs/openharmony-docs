# registerTypeDescriptors（系统接口）

## 导入模块

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
```

## registerTypeDescriptors

```TypeScript
function registerTypeDescriptors(typeDescriptors: Array<TypeDescriptor>): Promise<void>
```

注册一组标准化数据类型到系统中。使用Promise异步回调。注册成功后，标准化数据类型将被系统管理，可通过UDMF框架在其他应用或设备间共享和识别。  
**配对调用：**  
- 调用本接口注册类型后，注册的类型会占用系统资源，建议在应用退出或类型不再使用时调用unregisterTypeDescriptors()接口及时注销。

**起始版本：** 22

**需要权限：** ohos.permission.MANAGE_DYNAMIC_UTD_TYPE

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typeDescriptors | Array&lt;[TypeDescriptor](arkts-arkdata-uniformtypedescriptor-typedescriptor-c.md)&gt; | 是 | 注册的标准化数据类型描述符列表。TypeDescriptor用于描述自定义数据类型的属性，包括类型标识、所属类型、文件扩展名、MIME类型等。列表不可为空， 其中元素个数不超过50。单个应用注册的标准化数据类型描述符数量总计不超过200。    **TypeDescriptor格式要求：**  1.typeId不可为空字符串，长度不超过127，且仅包含字母、数字、中划线（-）和点号（.）。  2.belongingToTypes中元素个数不超过50。每项不可为空字符串，长度不超过127。  3.description/referenceURL/iconFile每项长度不超过255。 4.filenameExtensions中元素个数不超过50。每项不可为空字符串，长度不超过127且首字符必须为点号。  5.mimeTypes中元素个数不超过50。每项不可为空字符串，长度不超过127。    **TypeDescriptor内容要求：**  1.typeId必须唯一，不能与已注册类型的typeId重复。 2.typeId必须以当前应用的包名开头。 3.belongingToTypes中的标准化数据类型ID必须为预置数据类型或本次注册的其他标准化数据类型的typeId。  4.标准化数据类型之间不能存在循环依赖关系。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [20400002](../errorcode-udmf.md#20400002-标准化数据类型描述符格式错误) | The format of one or more typeDescriptors are invalid. |
| [20400003](../errorcode-udmf.md#20400003-标准化数据类型描述符内容错误) | The content of one or more typeDescriptors violate rules. |
