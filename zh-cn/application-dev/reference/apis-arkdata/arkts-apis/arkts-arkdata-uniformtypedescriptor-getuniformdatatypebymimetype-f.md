# getUniformDataTypeByMIMEType

## 导入模块

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
```

## getUniformDataTypeByMIMEType

```TypeScript
function getUniformDataTypeByMIMEType(mimeType: string, belongsTo?: string): string
```

根据给定的MIME类型和所归属的标准化数据类型查询标准化数据类型ID，若有多个符合条件的标准化数据类型ID，则返回第一个。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uniformTypeDescriptor-function getUniformDataTypeByMIMEType(mimeType: string, belongsTo?: string): string--><!--Device-uniformTypeDescriptor-function getUniformDataTypeByMIMEType(mimeType: string, belongsTo?: string): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mimeType | string | 是 | MIME类型名称，格式为'type/subtype'，如'image/jpeg'、'text/plain'等。 |
| belongsTo | string | 否 | 要查询的标准化数据类型所归属类型ID。无默认值，若不传入此参数则只按照MIME类型名称查询[标准化数据类型ID]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回与MIME类型名称以及归属类型ID（如果设置了belongsTo参数）匹配的标准化数据类型ID，如果要查询的标准化数据类型不存在则返回根据入参按指定规则生成的动态类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types;<br>3. Parameter verification failed. |

**示例：**

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let typeId = uniformTypeDescriptor.getUniformDataTypeByMIMEType('image/jpeg', 'general.image');
  if (typeId) {
    console.info('typeId is general.jpeg');
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`getUniformDataTypeByMIMEType throws an exception. code is ${error.code}, message is ${error.message} `);
}

// 根据“image/myimage”, “general.image”查不到预置数据类型则按返回根据入参信息生成的动态类型。
try {
  let typeId = uniformTypeDescriptor.getUniformDataTypeByMIMEType('image/myimage', 'general.image');
  if (typeId) {
    console.info('typeId is flex.************');
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`getUniformDataTypeByMIMEType throws an exception. code is ${error.code}, message is ${error.message} `);
}

```

