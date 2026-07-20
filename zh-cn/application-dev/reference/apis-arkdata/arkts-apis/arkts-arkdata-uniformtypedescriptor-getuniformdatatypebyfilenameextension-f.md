# getUniformDataTypeByFilenameExtension

## 导入模块

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
```

<a id="getuniformdatatypebyfilenameextension"></a>
## getUniformDataTypeByFilenameExtension

```TypeScript
function getUniformDataTypeByFilenameExtension(filenameExtension: string, belongsTo?: string): string
```

根据给定的文件后缀名和所归属的标准化数据类型查询标准化数据类型ID，若有多个符合条件的标准化数据类型ID，则返回第一个。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uniformTypeDescriptor-function getUniformDataTypeByFilenameExtension(filenameExtension: string, belongsTo?: string): string--><!--Device-uniformTypeDescriptor-function getUniformDataTypeByFilenameExtension(filenameExtension: string, belongsTo?: string): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filenameExtension | string | 是 | 文件后缀名称，需要包含点号，如'.ts'、'.jpg'等。 |
| belongsTo | string | 否 | 要查询的标准化数据类型所归属类型ID，用于限定查询范围。当需要查询特定归属类型下的数据类型时传入此参数，无默认值，若不传入此参数则只按照文件后缀名称查询[标准化数据类型ID]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回与给定文件后缀名以及归属类型ID（如果设置了belongsTo参数）匹配的标准化数据类型ID。如果要查询的标准化数据类型不存在，则返回根据入参按指定规则生成的动态类型（动态类型是系统动态生成的类型标识，以'flex.'为前缀，用于表示未预定义的数据类型）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types;<br>3. Parameter verification failed. |

**示例：**

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let typeId = uniformTypeDescriptor.getUniformDataTypeByFilenameExtension('.ts', 'general.source-code');
  if (typeId) {
    console.info('typeId is general.type-script');
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`getUniformDataTypeByFilenameExtension throws an exception. code is ${error.code}, message is ${error.message} `);
}

// 根据“.myts”，“general.plain-text”查不到预置数据类型则按返回根据入参信息生成的动态类型。
try {
  let typeId = uniformTypeDescriptor.getUniformDataTypeByFilenameExtension('.myts', 'general.plain-text');
  if (typeId) {
    console.info('typeId is flex.************');
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`getUniformDataTypeByFilenameExtension throws an exception. code is ${error.code}, message is ${error.message} `);
}

```

