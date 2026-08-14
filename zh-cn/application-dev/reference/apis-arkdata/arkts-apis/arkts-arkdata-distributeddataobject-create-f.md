# create

## create

```TypeScript
function create(context: Context, source: object): DataObject
```

创建一个分布式数据对象。对象属性支持基本类型（数字类型、布尔类型和字符串类型）以及复杂类型（数组、基本类型嵌套）。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-distributedDataObject-function create(context: Context, source: object): DataObject--><!--Device-distributedDataObject-function create(context: Context, source: object): DataObject-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用的上下文。 &lt;br&gt;FA模型的应用Context定义见Context。 &lt;br&gt;Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md#UIAbilityContext)。 |
| source | object | 是 | 设置分布式数据对象的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataObject](arkts-arkdata-distributeddataobject-dataobject-i.md) | 创建完成的分布式数据对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

## 示例

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

