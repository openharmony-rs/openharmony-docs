# create

## create

```TypeScript
function create(context: Context, source: object): DataObject
```

创建一个分布式数据对象。对象属性支持基本类型（数字类型、布尔类型和字符串类型）以及复杂类型（数组、基本类型嵌套）。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-distributedDataObject-function create(context: Context, source: object): DataObject--><!--Device-distributedDataObject-function create(context: Context, source: object): DataObject-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 应用的上下文。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_FA模型的应用Context定义见[Context]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Stage模型的应用Context定义见[Context]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| source | object | 是 | 设置分布式数据对象的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 创建完成的分布式数据对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |

**示例：**

FA模型示例：

```TypeScript
// 导入模块
import { featureAbility } from '@kit.AbilityKit';
// 获取context
let context = featureAbility.getContext();
class SourceObject {
  name: string
  age: number
  isVis: boolean

  constructor(name: string, age: number, isVis: boolean) {
    this.name = name;
    this.age = age;
    this.isVis = isVis;
  }
}

let source: SourceObject = new SourceObject('jack', 18, false);
let g_object: distributedDataObject.DataObject = distributedDataObject.create(context, source);
```

ArkTS-Dyn示例：

```TypeScript
// 导入模块
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let g_object: distributedDataObject.DataObject|null = null;

class SourceObject {
  name: string
  age: number
  isVis: boolean

  constructor(name: string, age: number, isVis: boolean) {
    this.name = name;
    this.age = age;
    this.isVis = isVis;
  }
}

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let source: SourceObject = new SourceObject('jack', 18, false);
        g_object = distributedDataObject.create(this.context, source);
    }
}
```

ArkTS-Sta示例：

```TypeScript
// 导入模块
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import distributedDataObject from '@ohos.data.distributedDataObject';

let g_object: distributedDataObject.DataObject | null = null;

class SourceObject {
  name: string
  age: int
  isVis: boolean

  constructor(name: string, age: int, isVis: boolean) {
    this.name = name;
    this.age = age;
    this.isVis = isVis;
  }
}

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let source: SourceObject = new SourceObject('jack', 18, false);
    g_object = distributedDataObject.create(this.context, source);
  }
}
```

