# canBeObserved接口：判断对象是否可被观察

为了判断对象是否为可被观察对象和获取对象关联的组件信息，开发者可以使用[canBeObserved接口](../../reference/apis-arkui/js-apis-stateManagement-static.md#canbeobserved24)。

>**说明：**
>
> 从API version 24开始，开发者可以在ArkTS-Sta中使用UIUtils的canBeObserved接口判断数据对象是否为可观察对象。

## 概述

在开发和调试过程中，开发者可能会遇到修改对象的值后UI页面不刷新的问题，在复杂业务中排查此类问题尤为不便。为此，提供了canBeObserved接口帮助开发者定位和分析问题。开发者使用该接口不仅可以判断对象是否为可被观察的对象，还能获取对象关联的组件信息。

在ArkTS-Sta中，使用canBeObserved接口需要导入UIUtils工具。

```ts
import { UIUtils } from '@kit.ArkUI';
```

## 限制条件

canBeObserved的入参需为对象类型。如果传入简单类型（如`int`、`string`、`boolean`）、`undefined`或`null`等非对象类型，canBeObserved会认为传入数据不可观察，返回值中`isObserved`值为false。

``` ts
import { UIUtils, Observed } from '@kit.ArkUI';

let res1 = UIUtils.canBeObserved(2); // 简单类型入参，认为不可观察，返回值isObserved为false
let res2 = UIUtils.canBeObserved(undefined); // undefined类型入参，认为不可观察，返回值isObserved为false
let res3 = UIUtils.canBeObserved(null); // null类型入参，认为不可观察，返回值isObserved为false

@Observed
class User {
  name?: string;
}

let result: ObservedResult = UIUtils.canBeObserved(new User()); // 正确用法，传入对象类型
```

## 对象可被观察场景

在ArkTS-Sta中，状态管理定义的可观察对象共有四种情况，与调用canBeObserved接口，返回的[ObservedResult](../../reference/apis-arkui/js-apis-stateManagement-static.md#observedresult24)结果对象中`reason`的值对应。

| 可观察场景         | reason值                                                     | 说明                                                         |
| ------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| @Observed/@Track   | The object data is decorated with @Observed.                 | 对象被[@Observed](./arkts-static-observed-and-objectlink.md)装饰器装饰，或对象属性被[@Track](./arkts-static-track.md)装饰器装饰。 |
| @ObservedV2/@Trace | The object data is decorated with V2 @ObservedV2 and @Trace. | 对象和对象属性被[@ObservedV2和@Trace](./arkts-static-new-observedV2-and-trace.md)装饰器装饰。 |
| ObjectLiteral(interface字面量)      | The object data is object literal decorated with V1 decorators or wrapped by makeObserved. | 对象为interface实例，且实例由状态管理V1装饰器装饰或经过[makeObserved](../../reference/apis-arkui/js-apis-stateManagement-static.md#makeobserved)方法包装。 |
| Built-in(Array/Map/Set/Date) | The object data is built-in type data (Array/Map/Set/Date) decorated with V1/V2 decorators or wrapped by makeObserved. | Array、Set、Map、Date类型数据对象由状态管理V1/V2装饰器装饰或经过makeObserved方法包装。 |

需要注意，上述情况`reason`的值结尾如果有`but not used in UI`则表示：对象虽然是可被观察的，但是没有被UI组件所使用，因此改变对象值的时候也无法触发UI刷新。

### @Observed/@Track观察场景

在ArkTS-Sta中，被@Observed装饰或被@Track装饰对象属性的class实例具有被观察的能力。根据对象所用于的组件，又可以分为在V1自定义组件中使用与在V2自定义组件中使用：
- 在V1自定义组件中使用时，class实例需要被组件内状态管理V1装饰器装饰，才能被观察到变化。
- 在V2自定义组件中使用时，class实例无需其他装饰器装饰，也能被观察到变化。

其中状态管理V1装饰器指：[@State](./arkts-static-state.md)、[@PropRef](./arkts-static-propref.md)、[@Link](./arkts-static-link.md)、[@ObjectLink](./arkts-static-observed-and-objectlink.md)、[@StorageLink](./arkts-static-appstorage.md#storagelink)、[@StoragePropRef](./arkts-static-appstorage.md#storagepropref)、[@LocalStorageLink](./arkts-static-localstorage.md#localstoragelink)、[@LocalStoragePropRef](./arkts-static-localstorage.md#localstoragepropref)、[@Provide](./arkts-static-provide-and-consume.md)、[@Consume](./arkts-static-provide-and-consume.md)。

以@Observed为例，@Observed装饰的class实例被@State装饰并用在UI上时，调用canBeObserved接口将获取到以下信息。

示例代码：
``` ts
'use static'

import { Entry, Text, Column, Component, Button, State, UIUtils, Observed } from '@kit.ArkUI'

@Observed
class Info {
  age: int = 25;
  name: string = 'Tom'
}
@Entry
@Component
struct Index {
  @State info: Info = new Info(); // @Observed装饰的对象实例被@State装饰

  build() {
    Column() {
      Button('show observed result')
        .backgroundColor('#FFFF00FF')
        .onClick(() => {
          console.info(`observed result: ${JSON.stringify(UIUtils.canBeObserved(this.info))}`); // 获取是否可观察信息
        })
      Text(`name: ${this.info.name}`).fontSize(20)
    }
  }
}
```
canBeObserved接口返回信息：
``` json5
{
	"reason": "The object data is decorated with @Observed",
	"isObserved": true,
	"decoratorInfo": [{
		"decoratorName": "@State",
		"dependentInfo": [{
			"elementId": 6,
			"elementName": "Text"
		}],
		"owningComponentId": 2,
		"stateVariableName": "info",
		"owningComponentOrClassName": "Index"
	}]
}
```
若使用@Track，此时将以@Track装饰的属性维度展示属性与组件的绑定关系。

示例代码：
``` ts
'use static'

import { Entry, Text, Column, Component, Button, State, UIUtils, Observed, Track } from '@kit.ArkUI'

@Observed
class Info {
  @Track age: int = 25; // 对象属性被@Track装饰
  @Track name: string = 'Tom'
}
@Entry
@Component
struct Index {
  @State info: Info = new Info();

  build() {
    Column() {
      Button('show observed result')
        .backgroundColor('#FFFF00FF')
        .onClick(() => {
          console.info(`observed result: ${JSON.stringify(UIUtils.canBeObserved(this.info))}`); // 获取是否可观察信息
        })
      Text(`name: ${this.info.name}`).fontSize(20)
      Text(`age: ${this.info.age}`).fontSize(20)
    }
  }
}
```
canBeObserved接口返回信息：
``` json5
{
	"reason": "The object data is decorated with @Observed",
	"isObserved": true,
	"decoratorInfo": [{
			"decoratorName": "@Track",
			"dependentInfo": [{
				"elementId": 7,
				"elementName": "Text"
			}],
			"owningComponentId": -1,
			"stateVariableName": "age",
			"owningComponentOrClassName": "Info"
		},
		{
			"decoratorName": "@Track",
			"dependentInfo": [{
				"elementId": 6,
				"elementName": "Text"
			}],
			"owningComponentId": -1,
			"stateVariableName": "name",
			"owningComponentOrClassName": "Info"
		}
	]
}
```
若在V2自定义组件中使用，将以对象整体的维度展示对象与组件的绑定关系。

示例代码：
``` ts
'use static'

import { Entry, Text, Column, Component, ComponentV2, Button, State, UIUtils, Observed, Param, Require } from '@kit.ArkUI'

@Observed
class Info {
  age: int = 25;
  name: string = 'Tom'
}
@Entry
@Component
struct Index {
  @State info: Info = new Info();

  build() {
    Column() {
      Button('show observed result')
        .backgroundColor('#FFFF00FF')
        .onClick(() => {
          console.info(`observed result: ${JSON.stringify(UIUtils.canBeObserved(this.info))}`); // 获取是否可观察信息
        })
      Text(`name: ${this.info.name}`).fontSize(20)
      Text(`age: ${this.info.age}`).fontSize(20)
      ParamChild({info: this.info})
    }
  }
}
@ComponentV2
struct ParamChild {
  @Param @Require info: Info; // @Observed装饰的对象实例在V2中使用
  build() {
    Column() {
      Text(`V2 name: ${this.info.age}`)
      Text(`V2 name: ${this.info.name}`)
    }
  }
}
```
canBeObserved接口返回信息：
``` json5
{
	"reason": "The object data is decorated with @Observed",
	"isObserved": true,
	"decoratorInfo": [{
			"decoratorName": "@State",
			"dependentInfo": [{
					"elementId": 8,
					"elementName": "ParamChild"
				},
				{
					"elementId": 7,
					"elementName": "Text"
				},
				{
					"elementId": 6,
					"elementName": "Text"
				}
			],
			"owningComponentId": 2,
			"stateVariableName": "info",
			"owningComponentOrClassName": "Index"
		},
		{
			"decoratorName": "@Observed(mix used in V2)",
			"dependentInfo": [{
					"elementId": 12,
					"elementName": "Text"
				},
				{
					"elementId": 11,
					"elementName": "Text"
				}
			],
			"owningComponentId": -1,
			"stateVariableName": "Unknown @Observed Object Property",
			"owningComponentOrClassName": "Info"
		}
	]
}
```
### @ObservedV2/@Trace观察场景

在ArkTS-Sta中，被@ObservedV2装饰且属性被@Trace装饰的class实例具有被观察的能力。与@Track的场景类似，使用@Trace，仍将以@Trace装饰的属性维度展示属性与组件的绑定关系。

示例代码：
``` ts
'use static'

import { Entry, Text, Column, ComponentV2, Button, UIUtils, ObservedV2, Trace, Local } from '@kit.ArkUI'

@ObservedV2
class Info {
  @Trace age: int = 25;
  @Trace name: string = 'Tom'
}
@Entry
@ComponentV2
struct Index {
  @Local info: Info = new Info(); // @ObservedV2装饰的对象实例

  build() {
    Column() {
      Button('show observed result')
        .backgroundColor('#FFFF00FF')
        .onClick(() => {
          console.info(`observed result: ${JSON.stringify(UIUtils.canBeObserved(this.info))}`); // 获取是否可观察信息
        })
      Text(`name: ${this.info.name}`).fontSize(20)
      Text(`age: ${this.info.age}`).fontSize(20)
    }
  }
}
```
canBeObserved接口返回信息：
``` json5
{
	"reason": "The object data is decorated with V2 @ObservedV2 and @Trace",
	"isObserved": true,
	"decoratorInfo": [{
			"decoratorName": "@Trace",
			"dependentInfo": [{
				"elementId": 7,
				"elementName": "Text"
			}],
			"owningComponentId": -1,
			"stateVariableName": "age",
			"owningComponentOrClassName": "Info"
		},
		{
			"decoratorName": "@Trace",
			"dependentInfo": [{
				"elementId": 6,
				"elementName": "Text"
			}],
			"owningComponentId": -1,
			"stateVariableName": "name",
			"owningComponentOrClassName": "Info"
		}
	]
}
```
### ObjectLiteral观察场景

在ArkTS-Sta中，被状态管理V1装饰器装饰或makeObserved接口包装过的interface字面量具有被观察的能力。被V1状态管理装饰器装饰的interface字面量，又可以分为在V1自定义组件中使用与在V2自定义组件中使用：
- 在V1自定义组件中使用时，interface字面量需要直接被组件内状态管理V1装饰器装饰，才能被观察到变化。
- 在V2自定义组件中使用时，interface字面量无需其他装饰器装饰，也能被观察到变化，但需确保该字面量的观察能力来自于V1装饰器，即由V1装饰器装饰后再将该字面量从V1组件传递给V2组件使用。

其中状态管理V1装饰器指：[@State](./arkts-static-state.md)、[@PropRef](./arkts-static-propref.md)、[@Link](./arkts-static-link.md)、[@ObjectLink](./arkts-static-observed-and-objectlink.md)、[@StorageLink](./arkts-static-appstorage.md#storagelink)、[@StoragePropRef](./arkts-static-appstorage.md#storagepropref)、[@LocalStorageLink](./arkts-static-localstorage.md#localstoragelink)、[@LocalStoragePropRef](./arkts-static-localstorage.md#localstoragepropref)、[@Provide](./arkts-static-provide-and-consume.md)、[@Consume](./arkts-static-provide-and-consume.md)。

特别地，被@Trace装饰的对象将视为被makeObserved包装。

以V1装饰器为例，当interface字面量被V1装饰器装饰并使用在UI上时，调用canBeObserved接口将获取到以下信息。

示例代码：
``` ts
'use static'

import { Entry, Text, Column, Component, ComponentV2, Button, State, UIUtils, Param, Require } from '@kit.ArkUI'

interface Info {
  age: int;
  name: string;
}
@Entry
@Component
struct Index {
  @State info: Info = { age: 25, name: 'Tom' } as Info; // @State装饰的对象字面量

  build() {
    Column() {
      Button('show observed result')
        .backgroundColor('#FFFF00FF')
        .onClick(() => {
          console.info(`observed result: ${JSON.stringify(UIUtils.canBeObserved(this.info))}`); // 获取是否可观察信息
        })
      Text(`name: ${this.info.name}`).fontSize(20)
      Text(`age: ${this.info.age}`).fontSize(20)
      ParamChild({info: this.info})
    }
  }
}
@ComponentV2
struct ParamChild {
  @Param @Require info: Info;
  build() {
    Column() {
      Text(`V2 name: ${this.info.age}`)
      Text(`V2 name: ${this.info.name}`)
    }
  }
}
```
canBeObserved接口返回信息：
``` json5
{
	"reason": "The object data is object literal decorated with V1 decorators or wrapped by makeObserved",
	"isObserved": true,
	"decoratorInfo": [{
			"decoratorName": "@State",
			"dependentInfo": [{
					"elementId": 8,
					"elementName": "ParamChild"
				},
				{
					"elementId": 7,
					"elementName": "Text"
				},
				{
					"elementId": 6,
					"elementName": "Text"
				}
			],
			"owningComponentId": 2,
			"stateVariableName": "info",
			"owningComponentOrClassName": "Index"
		},
		{
			"decoratorName": "V1 Decorated ObjectLiteral(mix used in V2)",
			"dependentInfo": [{
					"elementId": 12,
					"elementName": "Text"
				},
				{
					"elementId": 11,
					"elementName": "Text"
				}
			],
			"owningComponentId": -1,
			"stateVariableName": "Unknown Object Literal Property",
			"owningComponentOrClassName": "entry$src$main$ets$pages$Index$Info$ObjectLiteral"
		}
	]
}
```
### Built-in观察场景

在ArkTS-Sta中，被V1/V2状态管理装饰器装饰或makeObserved接口包装过的built-in类型对象（Array/Map/Set/Date）具有被观察的能力。被V1状态管理装饰器装饰的Array/Map/Set/Date类型对象，又可以分为在V1自定义组件中使用与在V2自定义组件中使用：
- 在V1自定义组件中使用时，Array/Map/Set/Date类型对象需要直接被组件内状态管理V1装饰器装饰，才能被观察到变化。
- 在V2自定义组件中使用时，Array/Map/Set/Date类型对象无需其他装饰器装饰，也能被观察到变化，但需确保该类型对象的观察能力来自于V1装饰器，即由V1装饰器装饰后再将该类型对象从V1组件传递给V2组件使用。

其中状态管理V1装饰器指：[@State](./arkts-static-state.md)、[@PropRef](./arkts-static-propref.md)、[@Link](./arkts-static-link.md)、[@ObjectLink](./arkts-static-observed-and-objectlink.md)、[@StorageLink](./arkts-static-appstorage.md#storagelink)、[@StoragePropRef](./arkts-static-appstorage.md#storagepropref)、[@LocalStorageLink](./arkts-static-localstorage.md#localstoragelink)、[@LocalStoragePropRef](./arkts-static-localstorage.md#localstoragepropref)、[@Provide](./arkts-static-provide-and-consume.md)、[@Consume](./arkts-static-provide-and-consume.md)。状态管理V2装饰器指：[@Local](./arkts-static-new-local.md)、[@Param](./arkts-static-new-param.md)、[@Provider](./arkts-new-static-provider-and-consumer.md)、[@Consumer](./arkts-static-new-provider-and-consumer.md)。

特别地，被@Trace装饰的对象将视为被makeObserved包装。

以V1装饰器为例，当Array类型对象被V1装饰器装饰并使用在UI上时，调用canBeObserved接口将获取到以下信息。

示例代码：
``` ts
'use static'

import { Entry, Text, Column, Component, ComponentV2, Button, State, UIUtils, Param, Require } from '@kit.ArkUI'

@Entry
@Component
struct Index {
  @State arr: int[] = [1, 2, 3]; // @State装饰Array类型

  build() {
    Column() {
      Button('show observed result')
        .backgroundColor('#FFFF00FF')
        .onClick(() => {
          console.info(`observed result: ${JSON.stringify(UIUtils.canBeObserved(this.arr))}`); // 获取是否可观察信息
        })
      Text(`${this.arr}`).fontSize(20)
      ParamChild({arr: this.arr})
    }
  }
}
@ComponentV2
struct ParamChild {
  @Param @Require arr: int[];
  build() {
    Column() {
      Text(`V2 arr: ${this.arr}`).fontSize(20)
    }
  }
}
```
canBeObserved接口返回信息：
``` json5
{
	"reason": "The object data is built-in type data (Array/Map/Set/Date) decorated with V1/V2 decorators or wrapped by makeObserved",
	"isObserved": true,
	"decoratorInfo": [{
			"decoratorName": "@State",
			"dependentInfo": [{
					"elementId": 7,
					"elementName": "ParamChild"
				},
				{
					"elementId": 6,
					"elementName": "Text"
				}
			],
			"owningComponentId": 2,
			"stateVariableName": "arr",
			"owningComponentOrClassName": "Index"
		},
		{
			"decoratorName": "V1 Decorated BuiltInType(mix used in V2)",
			"dependentInfo": [{
				"elementId": 10,
				"elementName": "Text"
			}],
			"owningComponentId": -1,
			"stateVariableName": "__OB_ANY_INDEX",
			"owningComponentOrClassName": "Array"
		},
		{
			"decoratorName": "V1 Decorated BuiltInType(mix used in V2)",
			"dependentInfo": [{
				"elementId": 10,
				"elementName": "Text"
			}],
			"owningComponentId": -1,
			"stateVariableName": "__OB_LENGTH",
			"owningComponentOrClassName": "Array"
		}
	]
}
```

## ArkTS-Sta上状态管理不刷新问题分析

在ArkTS-Sta中，由于可观察对象的定义发生变化，因此当开发者发现从ArkTS-Dyn上迁移的代码不刷新时，可以使用canBeObserved接口辅助分析。

### 状态管理V1装饰器装饰普通对象不刷新场景

在ArkTS-Dyn中，开发者可以直接使用状态管理V1装饰器装饰对象实现在V1自定义组件中对对象一层属性变化的观察。而在ArkTS-Sta中，普通的class实例不再具备观察能力。

ArkTS-Dyn代码：
``` ts
import { UIUtils } from '@kit.ArkUI';
class Info {
  age: number = 25;
  name: string = 'Tom';
}
@Entry
@Component
struct Index {
  @State info: Info = new Info(); // Info对象实例直接被@State装饰，可观察一层属性的变化

  build() {
    Column() {
      Text(`age: ${this.info.age}`)
        .onClick(() => {
          this.info.age++;
        })
      Button('show observe result')
        .onClick(() => {
          console.info(`observed result: ${JSON.stringify(UIUtils.canBeObserved(this.info))}`); // 获取是否可观察信息
        })
    }
  }
}
```
canBeObserved接口返回信息：
``` json5
{
	"isObserved": true,
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
	"decoratorInfo": [{
		"decoratorName": "@State",
		"stateVariableName": "info",
		"owningComponentOrClassName": "Index",
		"owningComponentId": 4,
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 6
		}]
	}]
}
```
而相同的代码在ArkTS-Sta上，却无法观察。

ArkTS-Sta代码：
``` ts
'use static'

import { Entry, Text, Column, Component, Button, State, UIUtils } from '@kit.ArkUI'
class Info {
  age: number = 25;
  name: string = 'Tom';
}
@Entry
@Component
struct Index {
  @State info: Info = new Info(); // Info对象实例直接被@State装饰，无法观察一层属性的变化

  build() {
    Column() {
      Text(`age: ${this.info.age}`)
        .onClick(() => {
          this.info.age++;
        })
      Button('show observe result')
        .onClick(() => {
          console.info(`observed result: ${JSON.stringify(UIUtils.canBeObserved(this.info))}`); // 获取是否可观察信息
        })
    }
  }
}
```
canBeObserved接口返回信息：
``` json5
{
	"reason": "The object data is not an observable object",
	"isObserved": false,
	"decoratorInfo": []
}
```
为class添加@Observed装饰，或为属性添加@Track装饰后，对象属性方能被观察。

ArkTS-Sta代码：
``` ts
'use static'

import { Entry, Text, Column, Component, Button, State, UIUtils, Observed } from '@kit.ArkUI'
@Observed
class Info {
  age: number = 25;
  name: string = 'Tom';
}
@Entry
@Component
struct Index {
  @State info: Info = new Info(); // @Observed装饰的Info对象实例被@State装饰，可观察一层属性的变化

  build() {
    Column() {
      Text(`age: ${this.info.age}`)
        .onClick(() => {
          this.info.age++;
        })
      Button('show observe result')
        .onClick(() => {
          console.info(`observed result: ${JSON.stringify(UIUtils.canBeObserved(this.info))}`); // 获取是否可观察信息
        })
    }
  }
}
```
canBeObserved接口返回信息：
``` json5
{
	"reason": "The object data is decorated with @Observed",
	"isObserved": true,
	"decoratorInfo": [{
		"decoratorName": "@State",
		"dependentInfo": [{
			"elementId": 5,
			"elementName": "Text"
		}],
		"owningComponentId": 2,
		"stateVariableName": "info",
		"owningComponentOrClassName": "Index"
	}]
}
```