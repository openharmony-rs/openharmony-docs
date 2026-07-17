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

**起始版本：** 22

**需要权限：** ohos.permission.MANAGE_DYNAMIC_UTD_TYPE

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-uniformTypeDescriptor-function registerTypeDescriptors(typeDescriptors: Array<TypeDescriptor>): Promise<void>--><!--Device-uniformTypeDescriptor-function registerTypeDescriptors(typeDescriptors: Array<TypeDescriptor>): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typeDescriptors | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<TypeDescriptor> | 是 | 待注册的标准化数据类型描述符列表。TypeDescriptor用于描述自定义数据类型的属性，包括类型标识、所属类型、文件扩展名、MIME类型等。列表不可为空，其中元素个数不超过50。单个应用注册的标准化数据类型描述符数量总计不超过200。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [20400002](../errorcode-udmf.md#20400002-标准化数据类型描述符格式错误) | The format of one or more typeDescriptors are invalid. |
| [20400003](../errorcode-udmf.md#20400003-标准化数据类型描述符内容错误) | The content of one or more typeDescriptors violate rules. |

