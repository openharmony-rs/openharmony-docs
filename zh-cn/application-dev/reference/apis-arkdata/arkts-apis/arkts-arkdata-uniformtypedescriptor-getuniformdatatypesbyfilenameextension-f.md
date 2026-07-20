# getUniformDataTypesByFilenameExtension

## 导入模块

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
```

<a id="getuniformdatatypesbyfilenameextension"></a>
## getUniformDataTypesByFilenameExtension

```TypeScript
function getUniformDataTypesByFilenameExtension(filenameExtension: string, belongsTo?: string): Array<string>
```

根据给定的文件后缀名和所归属的标准化数据类型查询标准化数据类型ID列表。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uniformTypeDescriptor-function getUniformDataTypesByFilenameExtension(filenameExtension: string, belongsTo?: string): Array<string>--><!--Device-uniformTypeDescriptor-function getUniformDataTypesByFilenameExtension(filenameExtension: string, belongsTo?: string): Array<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filenameExtension | string | 是 | 文件后缀名称。 |
| belongsTo | string | 否 | 要查询的标准化数据类型所归属类型ID，无默认值，若不传入此参数则只按照文件后缀名称查询[标准化数据类型ID]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回与给定文件后缀名以及归属类型ID（如果设置了belongsTo参数）匹配的标准化数据类型ID列表，如果要查询的标准化数据类型不存在则返回根据入参按指定规则生成的动态类型列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types;<br>3. Parameter verification failed. |

**示例：**

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let typeIds = uniformTypeDescriptor.getUniformDataTypesByFilenameExtension('.ts', 'general.source-code');
  for (let typeId of typeIds) {
    console.info(`typeId is ${typeId}`);
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`getUniformDataTypesByFilenameExtension throws an exception. code is ${error.code}, message is ${error.message} `);
}

// 根据“.myts”，“general.plain-text”查不到预置数据类型则按返回根据入参信息生成的动态类型列表。
try {
  let flexTypeIds = uniformTypeDescriptor.getUniformDataTypesByFilenameExtension('.myts', 'general.plain-text');
  for (let flexTypeId of flexTypeIds) {
    console.info(`typeId is flex type, flex typeId is ${flexTypeId}`);
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`getUniformDataTypesByFilenameExtension throws an exception. code is ${error.code}, message is ${error.message} `);
}

```

