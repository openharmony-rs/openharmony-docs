# TypeDescriptor

标准化数据类型的描述类，它包含了一些属性和方法用于描述标准化数据类型自身以及和其他标准化数据类型之间的归属与层级关系，例如通过typeId与belongingToTypes维护类型映射关系，并提供层级判断等方法。详细属性与方法参见 下文说明。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
```

## belongsTo

```TypeScript
belongsTo(type: string): boolean
```

判断当前标准化数据类型是否归属于指定的标准化数据类型。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 所指定的标准化数据类型（即[UTD预置列表](../../../database/uniform-data-type-list.md)中各类型对应的UTD-ID或自定义UTD-ID）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前的标准化数据类型归属于所指定的标准化数据类型，包括所指定类型与当前类型相同的情况；返回false则表示无归属关系。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;  2.Incorrect parameter types;  3. Parameter verification failed. |

**示例**

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 获取TypeDescriptor对象
  let typeObj: uniformTypeDescriptor.TypeDescriptor = uniformTypeDescriptor.getTypeDescriptor('general.type-script');
  // 判断是否归属指定类型
  let ret = typeObj.belongsTo('general.source-code');
  if (ret) {
    console.info('type general.type-script belongs to type general.source-code');
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`belongsTo throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

## equals

```TypeScript
equals(typeDescriptor: TypeDescriptor): boolean
```

判断指定的标准化数据类型描述类对象的类型ID和当前标准化数据类型描述类对象的类型ID是否相同，即[TypeDescriptor](#typedescriptor)对象的 typeId。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typeDescriptor | [TypeDescriptor](arkts-arkdata-uniformtypedescriptor-typedescriptor-c.md) | 是 | 待比较的标准化数据类型描述类对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示所比较的两个TypeDescriptor相同；返回false则表示不同。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;  2.Incorrect parameter types;  3. Parameter verification failed. |

**示例**

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 获取两个TypeDescriptor对象进行比较
  let typeA: uniformTypeDescriptor.TypeDescriptor = uniformTypeDescriptor.getTypeDescriptor('general.type-script');
  let typeB: uniformTypeDescriptor.TypeDescriptor = uniformTypeDescriptor.getTypeDescriptor('general.python-script');
  if (!typeA.equals(typeB)) {
    console.info('typeA is not equal to typeB');
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

## isHigherLevelType

```TypeScript
isHigherLevelType(type: string): boolean
```

判断当前标准化数据类型是否是指定标准化数据类型的高层级类型。例如SOURCE_CODE为TYPE_SCRIPT的高层级类型，TEXT为SOURCE_CODE和TYPE_SCRIPT的高层级类型。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 所指定的标准化数据类型（即[UTD预置列表](../../../database/uniform-data-type-list.md)中各类型对应的UTD-ID或自定义UTD-ID）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前的标准化数据类型是所指定标准化数据类型的高层级类型，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;  2.Incorrect parameter types;  3. Parameter verification failed. |

**示例**

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 获取TypeDescriptor对象
  let typeObj: uniformTypeDescriptor.TypeDescriptor = uniformTypeDescriptor.getTypeDescriptor('general.source-code');
  let ret = typeObj.isHigherLevelType('general.type-script');
  if (ret) {
    console.info('type general.source-code is higher level type of type general.type-script');
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`isHigherLevelType throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

## isLowerLevelType

```TypeScript
isLowerLevelType(type: string): boolean
```

判断当前标准化数据类型是否是指定标准化数据类型的低层级类型。例如TYPE_SCRIPT为SOURCE_CODE的低层级类型，TYPE_SCRIPT和SOURCE_CODE为TEXT的低层级类型。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 所指定的标准化数据类型（即[UTD预置列表](../../../database/uniform-data-type-list.md)中各类型对应的UTD-ID或自定义UTD-ID）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前的标准化数据类型是所指定标准化数据类型的低层级类型，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;  2.Incorrect parameter types;  3. Parameter verification failed. |

**示例**

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 获取TypeDescriptor对象
  let typeObj: uniformTypeDescriptor.TypeDescriptor = uniformTypeDescriptor.getTypeDescriptor('general.type-script');
  let ret = typeObj.isLowerLevelType('general.source-code');
  if (ret) {
    console.info('type general.type-script is lower level type of type general.source-code');
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`isLowerLevelType throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

## belongingToTypes

```TypeScript
set belongingToTypes(value: Array<string>)
```

标准化数据类型所归属的类型typeId列表。

**类型：** Array&lt;string&gt;

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## description

```TypeScript
set description(value: string)
```

标准化数据类型的简要说明。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## filenameExtensions

```TypeScript
set filenameExtensions(value: Array<string>)
```

标准化数据类型所关联的文件名后缀列表。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## iconFile

```TypeScript
set iconFile(value: string)
```

标准化数据类型的默认图标文件路径，可能为空字符串（即没有默认图标），应用可以自行决定是否使用该默认图标。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## mimeTypes

```TypeScript
set mimeTypes(value: Array<string>)
```

标准化数据类型所关联的多用途互联网邮件扩展类型列表。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## referenceURL

```TypeScript
set referenceURL(value: string)
```

标准化数据类型的参考链接URL，用于描述类型的详细信息。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## typeId

```TypeScript
set typeId(value: string)
```

标准化数据类型的ID（即{@code UniformDataType}中各类型对应的UTD-ID），也可以是自定义UTD。自定义UTD建议使用反向域名格式（如'com.example.mytype'）。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core
