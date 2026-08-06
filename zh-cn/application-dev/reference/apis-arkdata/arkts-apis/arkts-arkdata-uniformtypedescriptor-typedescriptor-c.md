# TypeDescriptor

标准化数据类型的描述类，它包含了一些属性和方法用于描述标准化数据类型自身以及和其他标准化数据类型之间的归属与层级关系，例如通过typeId与belongingToTypes维护类型映射关系，并提供层级判断等方法。详细属性与方法参见 下文说明。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-uniformTypeDescriptor-class TypeDescriptor--><!--Device-uniformTypeDescriptor-class TypeDescriptor-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## belongsTo

```TypeScript
belongsTo(type: string): boolean
```

判断当前标准化数据类型是否归属于指定的标准化数据类型。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TypeDescriptor-belongsTo(type: string): boolean--><!--Device-TypeDescriptor-belongsTo(type: string): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 所指定的标准化数据类型（即\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中各类型对应的UTD-ID或自定义UTD-ID）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前的标准化数据类型归属于所指定的标准化数据类型，包括所指定类型与当前类型相同的情况；返回false则表示无归属关系。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Incorrect parameter types;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_3. Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try{
    let typeObj : uniformTypeDescriptor.TypeDescriptor = uniformTypeDescriptor.getTypeDescriptor('general.type-script');
    let ret = typeObj.belongsTo('general.source-code');
    if(ret) {
        console.info('type general.type-script belongs to type general.source-code');
    }
} catch(e) {
    let error: BusinessError = e as BusinessError;
    console.error(`belongsTo throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

ArkTS-Sta示例：

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let typeObj : uniformTypeDescriptor.TypeDescriptor | null = uniformTypeDescriptor.getTypeDescriptor('general.type-script');
    if (!typeObj) {
        console.info('TypeDescriptor not found');
        return;
    }
    let ret = typeObj.belongsTo('general.source-code');
    if(ret) {
        console.info('type general.type-script belongs to type general.source-code');
    }
} catch(e) {
    let error: BusinessError = e as BusinessError;
    console.info(`belongsTo throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

## equals

```TypeScript
equals(typeDescriptor: TypeDescriptor): boolean
```

判断指定的标准化数据类型描述类对象的类型ID和当前标准化数据类型描述类对象的类型ID是否相同，即[TypeDescriptor]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_对象的 typeId。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TypeDescriptor-equals(typeDescriptor: TypeDescriptor): boolean--><!--Device-TypeDescriptor-equals(typeDescriptor: TypeDescriptor): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typeDescriptor | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 待比较的标准化数据类型描述类对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示所比较的两个TypeDescriptor相同；返回false则表示不同。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Incorrect parameter types;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_3. Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let typeA: uniformTypeDescriptor.TypeDescriptor | null = uniformTypeDescriptor.getTypeDescriptor('general.type-script');
  if (!typeA) {
    console.info('TypeDescriptor not found');
    return;
  }
  let typeB: uniformTypeDescriptor.TypeDescriptor | null = uniformTypeDescriptor.getTypeDescriptor('general.python-script');
  if (!typeB) {
    console.info('TypeDescriptor not found');
    return;
  }
  if (!typeA.equals(typeB)) {
    console.info('typeA is not equal to typeB');
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.info(`throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

## isHigherLevelType

```TypeScript
isHigherLevelType(type: string): boolean
```

判断当前标准化数据类型是否是指定标准化数据类型的高层级类型。例如SOURCE\_CODE为TYPE\_SCRIPT的高层级类型，TEXT为SOURCE\_CODE和TYPE\_SCRIPT的高层级类型。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TypeDescriptor-isHigherLevelType(type: string): boolean--><!--Device-TypeDescriptor-isHigherLevelType(type: string): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 所指定的标准化数据类型（即\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中各类型对应的UTD-ID或自定义UTD-ID）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前的标准化数据类型是所指定标准化数据类型的高层级类型，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Incorrect parameter types;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_3. Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let typeObj: uniformTypeDescriptor.TypeDescriptor | null = uniformTypeDescriptor.getTypeDescriptor('general.source-code');
  if (!typeObj) {
    console.info('TypeDescriptor not found');
  }
  let ret = typeObj.isHigherLevelType('general.type-script');
  if (ret) {
    console.info('type general.source-code is higher level type of type general.type-script');
  }
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.info(`isHigherLevelType throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

## isLowerLevelType

```TypeScript
isLowerLevelType(type: string): boolean
```

判断当前标准化数据类型是否是指定标准化数据类型的低层级类型。例如TYPE\_SCRIPT为SOURCE\_CODE的低层级类型，TYPE\_SCRIPT和SOURCE\_CODE为TEXT的低层级类型。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TypeDescriptor-isLowerLevelType(type: string): boolean--><!--Device-TypeDescriptor-isLowerLevelType(type: string): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 所指定的标准化数据类型（即\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中各类型对应的UTD-ID或自定义UTD-ID）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前的标准化数据类型是所指定标准化数据类型的低层级类型，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Incorrect parameter types;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_3. Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try{
    let typeObj : uniformTypeDescriptor.TypeDescriptor = uniformTypeDescriptor.getTypeDescriptor('general.type-script');
    let ret = typeObj.isLowerLevelType('general.source-code');
    if(ret) {
        console.info('type general.type-script is lower level type of type general.source-code');
    }
} catch(e) {
    let error: BusinessError = e as BusinessError;
    console.error(`isLowerLevelType throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

ArkTS-Sta示例：

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let typeObj : uniformTypeDescriptor.TypeDescriptor | null = uniformTypeDescriptor.getTypeDescriptor('general.source-code');
    if (!typeObj) {
        console.info('TypeDescriptor not found');
        return;
    }
    let ret = typeObj.isLowerLevelType('general.source-code');
    if(ret) {
        console.info('type general.source-code is lower level type of type general.type-script');
    }
} catch(e) {
    let error: BusinessError = e as BusinessError;
    console.info(`isLowerLevelType throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

## belongingToTypes

```TypeScript
set belongingToTypes(value: Array<string>)
```

标准化数据类型所归属的类型typeId列表。

**类型：** Array&lt;string&gt;

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TypeDescriptor-set belongingToTypes(value: Array<string>)--><!--Device-TypeDescriptor-set belongingToTypes(value: Array<string>)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## description

```TypeScript
set description(value: string)
```

标准化数据类型的简要说明。

**类型：** string

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TypeDescriptor-set description(value: string)--><!--Device-TypeDescriptor-set description(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## filenameExtensions

```TypeScript
set filenameExtensions(value: Array<string>)
```

标准化数据类型所关联的文件名后缀列表。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TypeDescriptor-set filenameExtensions(value: Array<string>)--><!--Device-TypeDescriptor-set filenameExtensions(value: Array<string>)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## iconFile

```TypeScript
set iconFile(value: string)
```

标准化数据类型的默认图标文件路径，可能为空字符串（即没有默认图标），应用可以自行决定是否使用该默认图标。

**类型：** string

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TypeDescriptor-set iconFile(value: string)--><!--Device-TypeDescriptor-set iconFile(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## mimeTypes

```TypeScript
set mimeTypes(value: Array<string>)
```

标准化数据类型所关联的多用途互联网邮件扩展类型列表。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TypeDescriptor-set mimeTypes(value: Array<string>)--><!--Device-TypeDescriptor-set mimeTypes(value: Array<string>)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## referenceURL

```TypeScript
set referenceURL(value: string)
```

标准化数据类型的参考链接URL，用于描述类型的详细信息。

**类型：** string

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TypeDescriptor-set referenceURL(value: string)--><!--Device-TypeDescriptor-set referenceURL(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## typeId

```TypeScript
set typeId(value: string)
```

标准化数据类型的ID（即{@code UniformDataType}中各类型对应的UTD-ID），也可以是自定义UTD。自定义UTD建议使用反向域名格式（如'com.example.mytype'）。

**类型：** string

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TypeDescriptor-set typeId(value: string)--><!--Device-TypeDescriptor-set typeId(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

