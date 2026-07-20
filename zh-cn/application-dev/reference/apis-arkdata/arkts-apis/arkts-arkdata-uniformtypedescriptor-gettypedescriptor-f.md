# getTypeDescriptor

## 导入模块

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
```

<a id="gettypedescriptor"></a>
## getTypeDescriptor

```TypeScript
function getTypeDescriptor(typeId: string): TypeDescriptor
```

按给定的标准化数据类型ID查询并返回对应的标准化数据类型描述类对象。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uniformTypeDescriptor-function getTypeDescriptor(typeId: string): TypeDescriptor--><!--Device-uniformTypeDescriptor-function getTypeDescriptor(typeId: string): TypeDescriptor-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typeId | string | 是 | [标准化数据类型ID]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TypeDescriptor](arkts-arkdata-uniformtypedescriptor-typedescriptor-c.md) | 返回标准化数据类型描述类对象。如果要查询的标准化数据类型不存在，则返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types;<br>3. Parameter verification failed. |

**示例：**

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 获取指定类型的TypeDescriptor对象
  let typeObj: uniformTypeDescriptor.TypeDescriptor =
    uniformTypeDescriptor.getTypeDescriptor('com.adobe.photoshop-image');
  if (typeObj) {
    let typeId = typeObj.typeId;
    let belongingToTypes = typeObj.belongingToTypes;
    let description = typeObj.description;
    let referenceURL = typeObj.referenceURL;
    let iconFile = typeObj.iconFile;
    let filenameExtensions = typeObj.filenameExtensions;
    let mimeTypes = typeObj.mimeTypes;
    console.info(`typeId: ${typeId}, belongingToTypes: ${belongingToTypes}, description: ${description}, referenceURL: ${referenceURL}, iconFile: ${iconFile}, filenameExtensions: ${filenameExtensions}, mimeTypes: ${mimeTypes}`);
  } else {
    console.info('type com.adobe.photoshop-image does not exist');
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`getTypeDescriptor throws an exception. code is ${error.code}, message is ${error.message} `);
}

```

