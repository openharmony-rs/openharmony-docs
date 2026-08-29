# unregisterTypeDescriptors（系统接口）

## 导入模块

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
```

## unregisterTypeDescriptors

```TypeScript
function unregisterTypeDescriptors(typeIds: Array<string>): Promise<void>
```

从系统中注销一个或多个标准化数据类型。使用Promise异步回调。注销后，该数据类型将不再被系统识别，依赖该数据类型的数据可能无法正常处理，请确保在注销前已清理相关数据依赖。  
**配对调用：**  
- 注销通过registerTypeDescriptors()接口注册的标准化数据类型。  
- 注销后，该类型将无法再被系统识别和使用。

**起始版本：** 22

**需要权限：** ohos.permission.MANAGE_DYNAMIC_UTD_TYPE

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typeIds | Array &lt;string&gt; | 是 | 待注销的typeId列表。列表不可为空，其中元素个数不超过50。每项长度不超过127。    **typeId约束限制：** 1.typeId对应的标准化数据类型必须在系统中已注册；  2.typeId必须以当前应用的包名开头；  3.typeId对应的标准化数据类型必须已通过registerTypeDescriptors接口注册。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [20400004](../errorcode-udmf.md#20400004-标准化数据类型id列表错误) | One or more typeIds are invalid or do not exist. |
