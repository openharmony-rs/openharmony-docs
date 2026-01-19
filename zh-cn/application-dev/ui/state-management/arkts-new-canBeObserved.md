# canBeObserved接口：判断对象是否可被观察
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

在开发和调试过程中，开发者会遇到修改对象的值后UI页面未刷新的问题，在复杂业务中排查此类问题尤为不便。为此，提供了[canBeObserved接口](../../reference/apis-arkui/js-apis-stateManagement.md#canbeobserved23)，开发者使用该接口不仅可以判断对象是否为可被观察的对象，还能获取对象关联的组件信息。

>**说明：**
>
>从API version 23开始，开发者可以使用UIUtils中的canBeObserved接口判断数据对象是否为可观察对象。

## V1使用场景

V1使用场景包括：@State、@Link、@Prop、@ObjectLink、@StorageLink、@LocalStorageLink、@StorageProp、@LocalStorageProp、@Provide、@Consume装饰器，和makeV1Observed方法。

### @State使用场景

[@State](./arkts-state.md)装饰器可收集到对象关联的系统组件和自定义组件。

示例代码：

<!-- @[v1_state](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1State.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class StateUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

@Entry
@Component
struct V1State {
  @State stateUser: StateUser = new StateUser('Aki');

  build() {
    Column({ space: 20 }) {

      Child01({ stateUser: this.stateUser })

      Child02({ stateUser: this.stateUser })

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.stateUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
export struct Child01 {
  @State stateUser: StateUser = new StateUser();

  build() {
    Column() {
      Text('Child01 ' + this.stateUser.name)

      Child03({ stateUser: this.stateUser })
    }
  }
}

@Component
export struct Child02 {
  @State stateUser: StateUser = new StateUser();

  build() {
    Column() {
      Text('Child02 ' + this.stateUser.name)
    }
  }
}

@Component
export struct Child03 {
  @State stateUser: StateUser = new StateUser();

  build() {
    Column() {
      Text('Child03 ' + this.stateUser.name)
    }
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // 可被观察的原因，使用@State装饰的对象是可被观察的对象
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // 装饰器信息
	"decoratorInfo": [{
        // 装饰器名称
		"decoratorName": "@State",
        // 装饰器装饰器的属性名称
		"stateVariableName": "stateUser",
        // 装饰器所在的组件名称
		"owningComponentOrClassName": "V1State",
        // 装饰器所在的组件id
		"owningComponentId": 62,
        // 对象关联的组件信息，@State可以收集到自定义组件和系统组件
		"dependentInfo": [{
          // 对象关联的组件名称
			"elementName": "Child01",
          // 对象关联的组件id
			"elementId": 64
		}, {
			"elementName": "Child02",
			"elementId": 65
		}]
	}, {
		"decoratorName": "@State",
		"stateVariableName": "stateUser",
		"owningComponentOrClassName": "Child01",
		"owningComponentId": 64,
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 69
		}, {
			"elementName": "Child03",
			"elementId": 70
		}]
	}, {
		"decoratorName": "@State",
		"stateVariableName": "stateUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 74
		}]
	}, {
		"decoratorName": "@State",
		"stateVariableName": "stateUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 70,
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 72
		}]
	}]
}
```

### @Prop使用场景

[@Prop](./arkts-prop.md)装饰器可收集到对象关联的系统组件和自定义组件。

示例代码：

<!-- @[v1_prop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1Prop.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class PropUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

@Entry
@Component
struct V1Prop {
  @State propUser: PropUser = new PropUser('Lion');

  build() {
    Column({ space: 20 }) {

      Child01({ propUser: this.propUser })

      Child02({ propUser: this.propUser })

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.propUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
export struct Child01 {
  @Prop propUser: PropUser = new PropUser();

  build() {
    Column() {
      Text('Child01 ' + this.propUser.name)

      // Child03是Child01的子组件，使用@Prop时，深拷贝的对象发生变更，无法收集
      Child03({ propUser: this.propUser })
    }
  }
}

@Component
export struct Child02 {
  @Prop propUser: PropUser = new PropUser();

  build() {
    Column() {
      Text('Child02 ' + this.propUser.name)
    }
  }
}

@Component
export struct Child03 {
  @Prop propUser: PropUser = new PropUser();

  build() {
    Column() {
      Text('Child03 ' + this.propUser.name)
    }
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // 使用@State装饰的对象是可被观察的对象
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // 装饰器信息，第一个装饰器收集父组件的@State，可参考@State使用场景
	"decoratorInfo": [{
		"decoratorName": "@State",
		"stateVariableName": "propUser",
		"owningComponentOrClassName": "V1Prop",  
		"owningComponentId": 62,
        // 对象关联的组件信息，@State可以收集到自定义组件和系统组件，Child03是Child01的子组件，使用@Prop时，深拷贝的对象发生变更，所以无法收集
		"dependentInfo": [{
			"elementName": "Child01",
			"elementId": 64
		}, {
			"elementName": "Child02",
			"elementId": 65
		}]
	}, {
        // 装饰器名称
		"decoratorName": "@Prop",
        // 装饰器装饰器的属性名称
		"stateVariableName": "propUser",
        // 装饰器所在的组件名称
		"owningComponentOrClassName": "Child01",
        // 装饰器所在的组件id
		"owningComponentId": 64,
        // 对象关联的组件信息，@Prop可以收集到自定义组件和系统组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 69
		}, {
			"elementName": "Child03",
			"elementId": 70
		}]
	}, {
		"decoratorName": "@Prop",
		"stateVariableName": "propUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 74
		}]
	}]
}
```

### @Link使用场景

[@Link](./arkts-link.md)装饰器可收集到对象关联的系统组件，无法收集自定义组件。

示例代码：

<!-- @[v1_link](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1Link.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class LinkUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

@Entry
@Component
struct V1Link {
  @State linkUser: LinkUser = new LinkUser('Jack');

  build() {
    Column({ space: 20 }) {

      Child01({ linkUser: this.linkUser })

      Child02({ linkUser: this.linkUser })

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.linkUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
export struct Child01 {
  @Link linkUser: LinkUser;

  build() {
    Column() {
      // 只调用了自定义组件，无法收集到组件信息
      Child03({ linkUser: this.linkUser })
    }
  }
}

@Component
export struct Child02 {
  @Link linkUser: LinkUser;

  build() {
    Column() {
      Text('Child02 ' + this.linkUser.name)
    }
  }
}

@Component
export struct Child03 {
  @Link linkUser: LinkUser;

  build() {
    Column() {
      Text('Child03 ' + this.linkUser.name)
    }
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // 使用@State装饰的对象是可被观察的对象
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // 装饰器信息，第一个装饰器收集父组件的@State，可参考@State使用场景
	"decoratorInfo": [{
		"decoratorName": "@State",
		"stateVariableName": "linkUser",
		"owningComponentOrClassName": "V1Link",
		"owningComponentId": 62,
        // 自定义子组件中使用@Link时，无法被收集到
		"dependentInfo": []
	}, {
        // 装饰器名称
		"decoratorName": "@Link",
        // 装饰器装饰的属性名称
		"stateVariableName": "linkUser",
        // 装饰器装所在的组件名称
		"owningComponentOrClassName": "Child01",
        // 装饰器装所在的组件id
		"owningComponentId": 64,
        // @Link装饰器只能收集系统组件，无法收集到自定义组件
		"dependentInfo": []
	}, {
		"decoratorName": "@Link",
		"stateVariableName": "linkUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 69,
        // @Link装饰器只能收集系统组件，无法收集到自定义组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 71
		}]
	}, {
		"decoratorName": "@Link",
		"stateVariableName": "linkUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
        // @Link装饰器只能收集系统组件，无法收集到自定义组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 73
		}]
	}]
}
```

### @ObjectLink使用场景

[@ObjectLink](./arkts-observed-and-objectlink.md)可收集到对象关联的系统组件和自定义组件。

示例代码：

<!-- @[v1_object_link](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1ObjectLink.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class ObjectLinkUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

@Entry
@Component
struct V1ObjectLink {
  @State objLinkUser: ObjectLinkUser = new ObjectLinkUser('Monkey');

  build() {
    Column({ space: 20 }) {

      Child01({ objLinkUser: this.objLinkUser })

      Child02({ objLinkUser: this.objLinkUser })

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.objLinkUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
export struct Child01 {
  @ObjectLink objLinkUser: ObjectLinkUser;

  build() {
    Column() {
      Text('Child01 ' + this.objLinkUser.name)

      Child03({ objLinkUser: this.objLinkUser })
    }
  }
}

@Component
export struct Child02 {
  @ObjectLink objLinkUser: ObjectLinkUser;

  build() {
    Column() {
      Text('Child02 ' + this.objLinkUser.name)

      Child03({ objLinkUser: this.objLinkUser })
    }
  }
}

@Component
export struct Child03 {
  @ObjectLink objLinkUser: ObjectLinkUser;

  build() {
    Column() {
      Text('Child03 ' + this.objLinkUser.name)
    }
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // 使用@State装饰的对象是可被观察的对象
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // 装饰器信息，第一个装饰器收集父组件的@State，可参考@State使用场景
	"decoratorInfo": [{
		"decoratorName": "@State",
		"stateVariableName": "objLinkUser",
		"owningComponentOrClassName": "V1ObjectLink",
		"owningComponentId": 62,
		"dependentInfo": [{
			"elementName": "Child01",
			"elementId": 64
		}, {
			"elementName": "Child02",
			"elementId": 65
		}]
	}, {
        // 装饰器名称
		"decoratorName": "@ObjectLink",
        // 装饰器装饰的属性名称
		"stateVariableName": "objLinkUser",
        // 装饰器所在的组件名称
		"owningComponentOrClassName": "Child01",
        // 装饰器所在的组件id
		"owningComponentId": 64,
        // 对象关联的组件信息，@ObjectLink可收集系统组件和自定义组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 69
		}, {
			"elementName": "Child03",
			"elementId": 70
		}]
	}, {
		"decoratorName": "@ObjectLink",
		"stateVariableName": "objLinkUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 74
		}, {
			"elementName": "Child03",
			"elementId": 75
		}]
	}, {
		"decoratorName": "@ObjectLink",
		"stateVariableName": "objLinkUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 70,
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 72
		}]
	}, {
		"decoratorName": "@ObjectLink",
		"stateVariableName": "objLinkUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 75,
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 77
		}]
	}]
}
```

### @StorageLink使用场景

[@StorageLink](./arkts-appstorage.md#storagelink)可收集到对象关联的系统组件，无法收集自定义组件。

示例代码：

<!-- @[v1_storage_link](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1StorageLink.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class StorageLinkUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

AppStorage.setOrCreate('user', new StorageLinkUser('Lee'));

@Entry
@Component
struct V1StorageLink {
  @StorageLink('user') storageLinkUser: StorageLinkUser = new StorageLinkUser();

  build() {
    Column({ space: 20 }) {

      Child01()

      Child02()

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.storageLinkUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
export struct Child01 {
  @StorageLink('user') storageLinkUser: StorageLinkUser = new StorageLinkUser();

  build() {
    Column() {
      Text('Child01 ' + this.storageLinkUser.name)

      Child03()
    }
  }
}

@Component
export struct Child02 {
  @StorageLink('user') storageLinkUser: StorageLinkUser = new StorageLinkUser();

  build() {
    Column() {
      Text('Child02 ' + this.storageLinkUser.name)
    }
  }
}

@Component
export struct Child03 {
  @StorageLink('user') storageLinkUser: StorageLinkUser = new StorageLinkUser();

  build() {
    Column() {
      Text('Child03 ' + this.storageLinkUser.name)
    }
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // 使用@StorageLink装饰的对象是可被观察的对象
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // 装饰器信息
	"decoratorInfo": [{
        // 默认将@StorageLink装饰器的别名添加一个@State装饰器
		"decoratorName": "@State",
		"stateVariableName": "user",
		"owningComponentOrClassName": "",
		"dependentInfo": []
	}, {
        // 装饰器名称
		"decoratorName": "@StorageLink",
        // 装饰器装饰的属性名称
		"stateVariableName": "storageLinkUser",
        // 装饰器所在的组件名称
		"owningComponentOrClassName": "V1StorageLink",
        // 装饰器所在的组件id
		"owningComponentId": 62,
        // @StorageLink装饰器只能收集系统组件
		"dependentInfo": []
	}, {
		"decoratorName": "@StorageLink",
		"stateVariableName": "storageLinkUser",
		"owningComponentOrClassName": "Child01",
		"owningComponentId": 64,
        // @StorageLink装饰器只能收集系统组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 69
		}]
	}, {
		"decoratorName": "@StorageLink",
		"stateVariableName": "storageLinkUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
        // @StorageLink装饰器只能收集系统组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 74
		}]
	}, {
		"decoratorName": "@StorageLink",
		"stateVariableName": "storageLinkUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 70,
        // @StorageLink装饰器只能收集系统组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 72
		}]
	}]
}
```

### @StorageProp使用场景

[@StorageProp](./arkts-appstorage.md#storageprop)可收集到对象关联的系统组件，无法收集自定义组件。

示例代码：

<!-- @[v1_storage_prop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1StorageProp.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class StoragePropUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

AppStorage.setOrCreate('propUser', new StoragePropUser('Flowers'));

@Entry
@Component
struct V1StorageProp {
  @StorageLink('propUser') storagePropUser: StoragePropUser = new StoragePropUser();

  build() {
    Column({ space: 20 }) {

      Child01()

      Child02()

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.storagePropUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
export struct Child01 {
  @StorageProp('propUser') storagePropUser: StoragePropUser = new StoragePropUser();

  build() {
    Column() {
      Text('Child01 ' + this.storagePropUser.name)

      Child03()
    }
  }
}

@Component
export struct Child02 {
  @StorageProp('propUser') storagePropUser: StoragePropUser = new StoragePropUser();

  build() {
    Column() {
      Text('Child02 ' + this.storagePropUser.name)
    }
  }
}

@Component
export struct Child03 {
  @StorageProp('propUser') storagePropUser: StoragePropUser = new StoragePropUser();

  build() {
    Column() {
      Text('Child03 ' + this.storagePropUser.name)
    }
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // 使用@StorageLink装饰的对象是可被观察的对象
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // 装饰器信息
	"decoratorInfo": [{
        // 默认将@StorageLink装饰器的别名添加一个@State装饰器
		"decoratorName": "@State",
		"stateVariableName": "propUser",
		"owningComponentOrClassName": "",
		"dependentInfo": []
	}, {
		"decoratorName": "@StorageLink",
		"stateVariableName": "storagePropUser",
		"owningComponentOrClassName": "V1StorageProp",
		"owningComponentId": 62,
		"dependentInfo": []
	}, {
        // 装饰器名称
		"decoratorName": "@StorageProp",
        // 装饰器装饰的属性名称
		"stateVariableName": "storagePropUser",
        // 装饰器所在的组件名称
		"owningComponentOrClassName": "Child01",
        // 装饰器所在的组件id
		"owningComponentId": 64,
        // @StorageProp装饰器只能收集系统组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 69
		}]
	}, {
		"decoratorName": "@StorageProp",
		"stateVariableName": "storagePropUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
        // @StorageProp装饰器只能收集系统组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 74
		}]
	}, {
		"decoratorName": "@StorageProp",
		"stateVariableName": "storagePropUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 70,
        // @StorageProp装饰器只能收集系统组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 72
		}]
	}]
}
```

### @LocalStorageLink使用场景

[@LocalStorageLink](./arkts-localstorage.md#localstoragelink)可收集到对象关联的系统组件，无法收集自定义组件。

示例代码：

<!-- @[v1_local_storage_link](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1LocalStorageLink.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class LocalStorageLinkUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

const storage = new LocalStorage();
storage.setOrCreate('localLinkUser', new LocalStorageLinkUser('Lorenz'));

@Entry(storage)
@Component
struct V1LocalStorageLink {
  @LocalStorageLink('localLinkUser') localUser: LocalStorageLinkUser = new LocalStorageLinkUser();

  build() {
    Column({ space: 20 }) {

      Child01()

      Child02()

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.localUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
export struct Child01 {
  @LocalStorageLink('localLinkUser') localUser: LocalStorageLinkUser = new LocalStorageLinkUser();

  build() {
    Column() {
      Child03()
    }
  }
}

@Component
export struct Child02 {
  @LocalStorageLink('localLinkUser') localUser: LocalStorageLinkUser = new LocalStorageLinkUser();

  build() {
    Column() {
      Text('Child02 ' + this.localUser.name)
    }
  }
}

@Component
export struct Child03 {
  @LocalStorageLink('localLinkUser') localUser: LocalStorageLinkUser = new LocalStorageLinkUser();

  build() {
    Column() {
      Text('Child03 ' + this.localUser.name)
    }
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // 使用@LocalStorageLink装饰的对象是可被观察对象
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // 装饰器信息
	"decoratorInfo": [{
        // 默认将@LocalStorageLink装饰器的别名添加一个@State装饰器
		"decoratorName": "@State",
		"stateVariableName": "localLinkUser",
		"owningComponentOrClassName": "",
		"dependentInfo": []
	}, {
        // 装饰器名称
		"decoratorName": "@LocalStorageLink",
        // 装饰器装饰的属性名称
		"stateVariableName": "localUser",
        // 装饰器所在的组件名称
		"owningComponentOrClassName": "V1LocalStorageLink",
        // 装饰器所在的组件id
		"owningComponentId": 62,
        // @LocalStorageLink装饰器只能收集系统组件
		"dependentInfo": []
	}, {
		"decoratorName": "@LocalStorageLink",
		"stateVariableName": "localUser",
		"owningComponentOrClassName": "Child01",
		"owningComponentId": 64,
        // @LocalStorageLink装饰器只能收集系统组件
		"dependentInfo": []
	}, {
		"decoratorName": "@LocalStorageLink",
		"stateVariableName": "localUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
        // @LocalStorageLink装饰器只能收集系统组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 73
		}]
	}, {
		"decoratorName": "@LocalStorageLink",
		"stateVariableName": "localUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 69,
        // @LocalStorageLink装饰器只能收集系统组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 71
		}]
	}]
}
```

### @LocalStorageProp使用场景

[@LocalStorageProp](./arkts-localstorage.md#localstorageprop)可收集到对象关联的系统组件，无法收集自定义组件。

示例代码：

<!-- @[v1_local_storage_prop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1LocalStorageProp.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class LocalStoragePropUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

const storage = new LocalStorage();
storage.setOrCreate('localPropUser', new LocalStoragePropUser('Camry'));

@Entry(storage)
@Component
struct V1LocalStorageProp {
  @LocalStorageLink('localPropUser') localStoragePropUser: LocalStoragePropUser = new LocalStoragePropUser();

  build() {
    Column({ space: 20 }) {

      Child01()

      Child02()

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.localStoragePropUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
export struct Child01 {
  @LocalStorageProp('localPropUser') localStoragePropUser: LocalStoragePropUser = new LocalStoragePropUser();

  build() {
    Column() {
      Child03()
    }
  }
}

@Component
export struct Child02 {
  @LocalStorageProp('localPropUser') localStoragePropUser: LocalStoragePropUser = new LocalStoragePropUser();

  build() {
    Column() {
      Text('Child02 ' + this.localStoragePropUser.name)
    }
  }
}

@Component
export struct Child03 {
  @LocalStorageProp('localPropUser') localStoragePropUser: LocalStoragePropUser = new LocalStoragePropUser();

  build() {
    Column() {
      Text('Child03 ' + this.localStoragePropUser.name)
    }
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // 使用@LocalStorageLink装饰的对象是可被观察对象
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // 装饰器信息
	"decoratorInfo": [{
       // 默认将@LocalStorageLink装饰器的别名添加一个@State装饰器
		"decoratorName": "@State",
		"stateVariableName": "localPropUser",
		"owningComponentOrClassName": "",
		"dependentInfo": []
	}, {
        // 装饰器名称
		"decoratorName": "@LocalStorageLink",
        // 装饰器装饰的属性名称
		"stateVariableName": "localStoragePropUser",
        // 装饰器所在的组件名称
		"owningComponentOrClassName": "V1LocalStorageProp",
        // 装饰器所在的组件id
		"owningComponentId": 62,
		"dependentInfo": []
	}, {
		"decoratorName": "@LocalStorageProp",
		"stateVariableName": "localStoragePropUser",
		"owningComponentOrClassName": "Child01",
		"owningComponentId": 64,
        // @LocalStorageProp装饰器只能收集系统组件
		"dependentInfo": []
	}, {
		"decoratorName": "@LocalStorageProp",
		"stateVariableName": "localStoragePropUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
        // @LocalStorageProp装饰器只能收集系统组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 73
		}]
	}, {
		"decoratorName": "@LocalStorageProp",
		"stateVariableName": "localStoragePropUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 69,
        // @LocalStorageProp装饰器只能收集系统组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 71
		}]
	}]
}
```

### @Provide和@Consume使用场景

[@Provide](./arkts-provide-and-consume.md)和[@Consume](./arkts-provide-and-consume.md)配套使用，两者都可收集到对象关联的系统组件，无法收集自定义组件。

示例代码：

<!-- @[v1_provide_and_consume](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1ProvideAndConsume.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class ProvideConsumeUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

@Entry
@Component
struct V1ProvideAndConsume {
  @Provide('ProvideUser') pcUser: ProvideConsumeUser = new ProvideConsumeUser('Jenny');

  build() {
    Column({ space: 20 }) {

      Child01()

      Child02()

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.pcUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
export struct Child01 {
  @Consume('ProvideUser') pcUser: ProvideConsumeUser = new ProvideConsumeUser();

  build() {
    Column() {
      Child03()
    }
  }
}

@Component
export struct Child02 {
  @Consume('ProvideUser') pcUser: ProvideConsumeUser = new ProvideConsumeUser();

  build() {
    Column() {
      Text('Child02 ' + this.pcUser.name)
    }
  }
}

@Component
export struct Child03 {
  @Consume('ProvideUser') pcUser: ProvideConsumeUser = new ProvideConsumeUser();

  build() {
    Column() {
      Text('Child03 ' + this.pcUser.name)
    }
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // 使用@Provide装饰的对象是可被观察的对象
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // 装饰器信息
	"decoratorInfo": [{
        // 装饰器名称
		"decoratorName": "@Provide",
        // 装饰器装饰的属性名称
		"stateVariableName": "pcUser",
        // 装饰器所在组件的名称
		"owningComponentOrClassName": "V1ProvideAndConsume",
        // 装饰器所在组件的id
		"owningComponentId": 62,
        // @Provide装饰器只能收集系统组件
		"dependentInfo": []
	}, {
		"decoratorName": "@Consume",
		"stateVariableName": "pcUser",
		"owningComponentOrClassName": "Child01",
		"owningComponentId": 64,
        // @Consume装饰器只能收集系统组件
		"dependentInfo": []
	}, {
		"decoratorName": "@Consume",
		"stateVariableName": "pcUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
        // @Consume装饰器只能收集系统组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 73
		}]
	}, {
		"decoratorName": "@Consume",
		"stateVariableName": "pcUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 69,
        // @Consume装饰器只能收集系统组件
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 71
		}]
	}]
}
```

### built-in类型数据使用场景

built-in类型包含：Array、Map、Set、Date类型。

示例代码：

<!-- @[v1_built_in](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1BuiltIn.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

// 提供判断对象是否为可被观察对象的方法
function test(obj: object): void {
  console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(obj))}`);
}

@Entry
@Component
struct V1BuiltIn {
  @State arr: string[] = [];
  @State map: Map<string, string> = new Map<string, string>();
  @State set: Set<string> = new Set<string>();
  @State date: Date = new Date();

  aboutToAppear(): void {
    this.arr = ['1', '2', '3'];
    this.map.set('a', '11');
    this.map.set('b', '22');
    this.map.set('c', '33');
    this.set.add('111');
    this.set.add('222');
    this.set.add('333');
    this.date = new Date('2025-12-12');
  }

  build() {
    Column({ space: 20 }) {

      Child01({ arr: this.arr })

      Child02({ map: this.map })

      Child03({ set: this.set })

      Child04({ date: this.date })

      Button('test arr')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          test(this.arr);
        })

      Button('test map')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          test(this.map);
        })

      Button('test set')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          test(this.set);
        })

      Button('test date')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          test(this.date);
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
export struct Child01 {
  @State arr: string[] = [];

  build() {
    Column() {
      ForEach(this.arr, (item: string) => {
        Text('Child01 ' + item)
      })
    }
  }
}

@Component
export struct Child02 {
  @State map: Map<string, string> = new Map<string, string>();

  build() {
    Column() {
      ForEach(Array.from(this.map), (item: object) => {
        Text('Child02 ' + JSON.stringify(item))
      })
    }
  }
}

@Component
export struct Child03 {
  @State set: Set<string> = new Set<string>();

  build() {
    Column() {
      ForEach(Array.from(this.set), (item: string) => {
        Text('Child03 ' + item)
      })
    }
  }
}

@Component
export struct Child04 {
  @State date: Date = new Date();

  build() {
    Column() {
      Text('Child03 year: ' + this.date.getFullYear())
      Text('Child03 month: ' + this.date.getMonth())
      Text('Child03 day: ' + this.date.getDate())
    }
  }
}
```

返回结果：

``` json
// Array类型结果，参考@State使用场景
{
	"isObserved": true,
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
	"decoratorInfo": [{
		"decoratorName": "@State",
		"stateVariableName": "arr",
		"owningComponentOrClassName": "V1BuiltIn",
		"owningComponentId": 62,
		"dependentInfo": [{
			"elementName": "Child01",
			"elementId": 64
		}]
	}, {
		"decoratorName": "@State",
		"stateVariableName": "arr",
		"owningComponentOrClassName": "Child01",
		"owningComponentId": 64,
		"dependentInfo": [{
			"elementName": "ForEach",
			"elementId": 77
		}]
	}]
}

// Map类型结果，参考@State使用场景
{
	"isObserved": true,
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
	"decoratorInfo": [{
		"decoratorName": "@State",
		"stateVariableName": "map",
		"owningComponentOrClassName": "V1BuiltIn",
		"owningComponentId": 62,
		"dependentInfo": [{
			"elementName": "Child02",
			"elementId": 65
		}]
	}, {
		"decoratorName": "@State",
		"stateVariableName": "map",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
		"dependentInfo": [{
			"elementName": "ForEach",
			"elementId": 85
		}]
	}]
}

// Set类型结果，参考@State使用场景
{
	"isObserved": true,
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
	"decoratorInfo": [{
		"decoratorName": "@State",
		"stateVariableName": "set",
		"owningComponentOrClassName": "V1BuiltIn",
		"owningComponentId": 62,
		"dependentInfo": [{
			"elementName": "Child03",
			"elementId": 66
		}]
	}, {
		"decoratorName": "@State",
		"stateVariableName": "set",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 66,
		"dependentInfo": [{
			"elementName": "ForEach",
			"elementId": 93
		}]
	}]
}

// Date类型结果，参考@State使用场景
{
	"isObserved": true,
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
	"decoratorInfo": [{
		"decoratorName": "@State",
		"stateVariableName": "date",
		"owningComponentOrClassName": "V1BuiltIn",
		"owningComponentId": 62,
		"dependentInfo": [{
			"elementName": "Child04",
			"elementId": 67
		}]
	}, {
		"decoratorName": "@State",
		"stateVariableName": "date",
		"owningComponentOrClassName": "Child04",
		"owningComponentId": 67,
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 101
		}, {
			"elementName": "Text",
			"elementId": 102
		}, {
			"elementName": "Text",
			"elementId": 103
		}]
	}]
}
```

### makeV1Observed使用场景

使用[makeV1Observed](./arkts-v1-v2-mixusage.md#makev1observed)方法转换的对象，根据子组件使用的装饰器收集对象关联的组件。

示例代码：

<!-- @[v1_makeV1Observed](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1MakeV1Observed.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class ObservedV1User {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

@Entry
@Component
struct V1MakeV1Observed {
  observedUser: ObservedV1User = UIUtils.makeV1Observed(new ObservedV1User('White'));

  build() {
    Column({ space: 20 }) {

      Child01({ observedUser: this.observedUser })

      Child02({ observedUser: this.observedUser })

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.observedUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
export struct Child01 {
  @State observedUser: ObservedV1User = new ObservedV1User();

  build() {
    Column() {
      Child03({ observedUser: this.observedUser })
    }
  }
}

@Component
export struct Child02 {
  @State observedUser: ObservedV1User = new ObservedV1User();

  build() {
    Column() {
      Text('Child02 ' + this.observedUser.name)
    }
  }
}

@Component
export struct Child03 {
  @State observedUser: ObservedV1User = new ObservedV1User();

  build() {
    Column() {
      Text('Child03 ' + this.observedUser.name)
    }
  }
}
```

返回结果：

``` json
// 参考@State使用场景
{
	"isObserved": true,
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
	"decoratorInfo": [{
		"decoratorName": "@State",
		"stateVariableName": "observedUser",
		"owningComponentOrClassName": "Child01",
		"owningComponentId": 69,
		"dependentInfo": [{
			"elementName": "Child03",
			"elementId": 74
		}]
	}, {
		"decoratorName": "@State",
		"stateVariableName": "observedUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 70,
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 78
		}]
	}, {
		"decoratorName": "@State",
		"stateVariableName": "observedUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 74,
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 76
		}]
	}]
}
```

## V2使用场景

V2使用场景包括：@Local、@Param、@Computed、@Monitor、@Provider、@Consumer装饰器，和makeObserved方法。

V2装饰器收集的方式与V1不同，V2对象一般与@ObservedV2和@Trace联合使用，
V2装饰器收集组件信息时，是按照对象的@Trace属性进行分类收集。举例如下：

``` TypeScript
// 定义Class
@ObservedV2
class Test {
  @Trace a?: string;
  @Trace b?: string;
  @Trace c?: string;
}
```
``` json
// 返回结果分析
{
	"isObserved": true,
	"reason": "The object data is decorated with V2 @ObservedV2 and @Trace",
    // 装饰器信息是按照@Trace装饰的属性进行分类
	"decoratorInfo": [{
		"decoratorName": "@Trace",
        // 对象中@Trace属性的名称
		"stateVariableName": "a",
		"owningComponentOrClassName": "TestClass",
		"owningComponentId": -1,
        // 同一个@Trace属性关联的组件信息集合在一起
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 4
		},{
			"elementName": "Text",
			"elementId": 5
		}]
	},{
		"decoratorName": "@Trace",
		"stateVariableName": "b",
		"owningComponentOrClassName": "TestClass",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 6
		}]
	},{
		"decoratorName": "@Trace",
		"stateVariableName": "c",
		"owningComponentOrClassName": "TestClass",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 7
		},{
			"elementName": "Text",
			"elementId": 8
		}]
	}]
}
```

### @Local使用场景

[@Local](./arkts-new-local.md)只能在当前组件进行初始化，所以只能收集当前组件的信息。

示例代码：

<!-- @[v2_local](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V2Local.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

@ObservedV2
class LocalUser {
  @Trace
  public name?: string;
  @Trace
  public age?: number;

  constructor(name?: string, age?: number) {
    this.name = name ?? '';
    this.age = age ?? 0;
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

@Entry
@ComponentV2
struct V2Local {
  @Local localUser: LocalUser = new LocalUser('Goat', 35);

  build() {
    Column({ space: 20 }) {

      Text('index ' + this.localUser.name)

      Text('index ' + this.localUser.age)

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.localUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // @ObservedV2装饰的对象是可被观察的对象
	"reason": "The object data is decorated with V2 @ObservedV2 and @Trace",
    // 装饰器信息，V2对象根据对象中被@Trace装饰的属性收集信息
	"decoratorInfo": [{
		"decoratorName": "@Trace",
        // 被@Trace装饰的属性名称
		"stateVariableName": "name",
        // V2可被观察对象的类名称
		"owningComponentOrClassName": "LocalUser",
        // V2默认返回-1
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 19,
			"elementName": "Text"
		}]
	}, {
		"decoratorName": "@Trace",
		"stateVariableName": "age",
		"owningComponentOrClassName": "LocalUser",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 20,
			"elementName": "Text"
		}]
	}]
}
```

### @Param使用场景

[@Param](./arkts-new-param.md)可收集到对象关联的系统组件，无法收集自定义组件。

示例代码：

<!-- @[v2_param](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V2Param.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

@ObservedV2
class ParamUser {
  @Trace
  public name?: string;
  @Trace
  public age?: number;

  constructor(name?: string, age?: number) {
    this.name = name ?? '';
    this.age = age ?? 0;
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

@Entry
@ComponentV2
struct V2Param {
  @Local paramUser: ParamUser = new ParamUser('Uranus', 26);

  build() {
    Column({ space: 20 }) {

      Child01({ paramUser: this.paramUser })

      Child02({ paramUser: this.paramUser })

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.paramUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@ComponentV2
export struct Child01 {
  @Param paramUser: ParamUser = new ParamUser();

  build() {
    Column() {
      Child03({ paramUser: this.paramUser })
    }
  }
}

@ComponentV2
export struct Child02 {
  @Param paramUser: ParamUser = new ParamUser();

  build() {
    Column() {
      Text('Child02 ' + this.paramUser.name)

      Child04({ paramUser: this.paramUser })
    }
  }
}

@ComponentV2
export struct Child03 {
  @Param paramUser: ParamUser = new ParamUser();

  build() {
    Column() {
      Text('Child03 ' + this.paramUser.name)
    }
  }
}

@ComponentV2
export struct Child04 {
  @Param paramUser: ParamUser = new ParamUser();

  build() {
    Column() {
      Text('Child04 ' + this.paramUser.age)
    }
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // ObservedV2装饰的对象是可被观察的对象
	"reason": "The object data is decorated with V2 @ObservedV2 and @Trace",
    // 装饰器信息，可参考@Local使用场景
	"decoratorInfo": [{
		"decoratorName": "@Trace",
		"stateVariableName": "name",
		"owningComponentOrClassName": "ParamUser",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 26,
			"elementName": "Text"
		}, {
			"elementId": 28,
			"elementName": "Text"
		}]
	}, {
		"decoratorName": "@Trace",
		"stateVariableName": "age",
		"owningComponentOrClassName": "ParamUser",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 31,
			"elementName": "Text"
		}]
	}]
}
```

### @Computed使用场景

[@Computed](./arkts-new-computed.md)可收集到对象关联的@Computed方法名称和方法id。

示例代码：

<!-- @[v2_computed](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V2Computed.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

@ObservedV2
class ComputedUser {
  @Trace
  public name?: string;
  @Trace
  public age?: number;

  constructor(name?: string, age?: number) {
    this.name = name ?? '';
    this.age = age ?? 0;
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

@Entry
@ComponentV2
struct V2Computed {
  @Local computedUser: ComputedUser = new ComputedUser('Shanks', 66);

  build() {
    Column({ space: 20 }) {

      Child01({ computedUser: this.computedUser })

      Child02({ computedUser: this.computedUser })

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.computedUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@ComponentV2
export struct Child01 {
  @Param computedUser: ComputedUser = new ComputedUser();

  @Computed
  get child01Name(): string {
    return this.computedUser.name as string;
  }

  @Computed
  get child01Age(): number {
    return this.computedUser.age as number;
  }

  build() {
    Column() {
      Child03({ computedUser: this.computedUser })
    }
  }
}

@ComponentV2
export struct Child02 {
  @Param computedUser: ComputedUser = new ComputedUser();

  @Computed
  get child02Name(): string {
    return this.computedUser.name as string;
  }

  build() {
    Column() {

    }
  }
}

@ComponentV2
export struct Child03 {
  @Param computedUser: ComputedUser = new ComputedUser();

  @Computed
  get child03Age(): number {
    return this.computedUser.age as number;
  }

  build() {
    Column() {

    }
  }
}

@ComponentV2
export struct Child04 {
  @Param computedUser: ComputedUser = new ComputedUser();

  @Computed
  get child04Name(): string {
    return this.computedUser.name as string;
  }

  @Computed
  get child04Age(): number {
    return this.computedUser.age as number;
  }

  build() {
    Column() {

    }
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // @ObservedV2装饰的对象是可被观察的对象
	"reason": "The object data is decorated with V2 @ObservedV2 and @Trace",
    // 装饰器信息，可参考@Local使用场景
	"decoratorInfo": [{
		"decoratorName": "@Trace",
		"stateVariableName": "name",
		"owningComponentOrClassName": "ComputedUser",
		"owningComponentId": -1,
        // 组件信息，V2装饰器可以收集@Computed方法名称和id
		"dependentInfo": [{
			"elementId": 68719476737,
			"elementName": "@Computed get child01Name"
		}, {
			"elementId": 68719476739,
			"elementName": "@Computed get child02Name"
		}]
	}, {
		"decoratorName": "@Trace",
		"stateVariableName": "age",
		"owningComponentOrClassName": "ComputedUser",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 68719476738,
			"elementName": "@Computed get child01Age"
		}, {
			"elementId": 68719476740,
			"elementName": "@Computed get child03Age"
		}]
	}]
}
```

### @Monitor使用场景

[@Monitor](./arkts-new-monitor.md)可收集到对象关联的@Monitor方法名称和方法id。

示例代码：

<!-- @[v2_monitor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V2Monitor.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

@ObservedV2
class MonitorUser {
  @Trace
  public name?: string;
  @Trace
  public age?: number;

  constructor(name?: string, age?: number) {
    this.name = name ?? '';
    this.age = age ?? 0;
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

@Entry
@ComponentV2
struct V2Monitor {
  @Local monitorUser: MonitorUser = new MonitorUser('Poseidon', 76);

  build() {
    Column({ space: 20 }) {

      Child01({ monitorUser: this.monitorUser })

      Child02({ monitorUser: this.monitorUser })

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.monitorUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@ComponentV2
export struct Child01 {
  @Param monitorUser: MonitorUser = new MonitorUser();

  @Monitor('monitorUser.name')
  onChild01NameChange(): void {
    console.info(TAG, `onChild01NameChange`);
  }

  @Monitor('monitorUser.age')
  onChild01AgeChange(): void {
    console.info(TAG, `onChild01AgeChange`);
  }

  build() {
    Column() {
      Child03({ monitorUser: this.monitorUser })
    }
  }
}

@ComponentV2
export struct Child02 {
  @Param monitorUser: MonitorUser = new MonitorUser();

  @Monitor('monitorUser.name')
  onChild02NameChange(): void {
    console.info(TAG, `onChild02NameChange`);
  }

  build() {
    Column() {

    }
  }
}

@ComponentV2
export struct Child03 {
  @Param monitorUser: MonitorUser = new MonitorUser();

  @Monitor('monitorUser.age')
  onChild03AgeChange(): void {
    console.info(TAG, `onChild03AgeChange`);
  }

  build() {
    Column() {

    }
  }
}

@ComponentV2
export struct Child04 {
  @Param monitorUser: MonitorUser = new MonitorUser();

  @Monitor('monitorUser.name')
  onChild04NameChange(): void {
    console.info(TAG, `onChild04NameChange`);
  }

  @Monitor('monitorUser.age')
  onChild04AgeChange(): void {
    console.info(TAG, `onChild04AgeChange`);
  }

  build() {
    Column() {

    }
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // @ObservedV2装饰的对象是可被观察的对象
	"reason": "The object data is decorated with V2 @ObservedV2 and @Trace",
    // 装饰器信息，可参考@Local使用场景
	"decoratorInfo": [{
		"decoratorName": "@Trace",
		"stateVariableName": "name",
		"owningComponentOrClassName": "MonitorUser",
		"owningComponentId": -1,
        // 组件信息，V2装饰器可以收集@Monitor方法名称和id
		"dependentInfo": [{
			"elementId": 281474976710657,
			"elementName": "@Monitor onChild01NameChange"
		}, {
			"elementId": 281474976710659,
			"elementName": "@Monitor onChild02NameChange"
		}]
	}, {
		"decoratorName": "@Trace",
		"stateVariableName": "age",
		"owningComponentOrClassName": "MonitorUser",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 281474976710658,
			"elementName": "@Monitor onChild01AgeChange"
		}, {
			"elementId": 281474976710660,
			"elementName": "@Monitor onChild03AgeChange"
		}]
	}]
}
```

### @Provider和@Consumer使用场景

[@Provider](./arkts-new-provider-and-consumer.md)和[@Consumer](./arkts-new-provider-and-consumer.md)配套使用，两者都可收集到对象关联的系统组件，无法收集自定义组件。

示例代码：

<!-- @[v2_provider_and_consumer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V2ProviderAndConsumer.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

@ObservedV2
class ProviderConsumerUser {
  @Trace
  public name?: string;
  @Trace
  public age?: number;

  constructor(name?: string, age?: number) {
    this.name = name ?? '';
    this.age = age ?? 0;
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

@Entry
@ComponentV2
struct V2ProviderAndConsumer {
  @Provider('ProviderUser') pcUser: ProviderConsumerUser = new ProviderConsumerUser('Mars', 145);

  build() {
    Column({ space: 20 }) {

      Child01()

      Child02()

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.pcUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@ComponentV2
export struct Child01 {
  @Consumer('ProviderUser') pcUser: ProviderConsumerUser = new ProviderConsumerUser();

  build() {
    Column() {
      Text('Child01 ' + this.pcUser.name)

      Child03()
    }
  }
}

@ComponentV2
export struct Child02 {
  @Consumer('ProviderUser') pcUser: ProviderConsumerUser = new ProviderConsumerUser();

  build() {
    Column() {
      Text('Child02 ' + this.pcUser.age)

      Child04()
    }
  }
}

@ComponentV2
export struct Child03 {
  @Consumer('ProviderUser') pcUser: ProviderConsumerUser = new ProviderConsumerUser();

  build() {
    Column() {
      Text('Child01 ' + this.pcUser.name)
    }
  }
}

@ComponentV2
export struct Child04 {
  @Consumer('ProviderUser') pcUser: ProviderConsumerUser = new ProviderConsumerUser();

  build() {
    Column() {
      Text('Child01 ' + this.pcUser.name)

      Text('Child01 ' + this.pcUser.age)
    }
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // @ObservedV2装饰的对象是可被观察的对象
	"reason": "The object data is decorated with V2 @ObservedV2 and @Trace",
    // 装饰器信息，可参考@Local使用场景
	"decoratorInfo": [{
		"decoratorName": "@Trace",
		"stateVariableName": "name",
		"owningComponentOrClassName": "ProviderConsumerUser",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 24,
			"elementName": "Text"
		}, {
			"elementId": 27,
			"elementName": "Text"
		}, {
			"elementId": 32,
			"elementName": "Text"
		}]
	}, {
		"decoratorName": "@Trace",
		"stateVariableName": "age",
		"owningComponentOrClassName": "ProviderConsumerUser",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 29,
			"elementName": "Text"
		}, {
			"elementId": 33,
			"elementName": "Text"
		}]
	}]
}
```

### makeObserved使用场景

使用[makeObserved](./arkts-new-makeObserved.md)方法封装的对象，可收集到对象关联的系统组件，无法收集自定义组件。

示例代码：

<!-- @[v2_make_observed](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V2MakeObserved.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class MakeObservedUser {
  public name?: string;
  public age?: number;

  constructor(name?: string, age?: number) {
    this.name = name ?? '';
    this.age = age ?? 0;
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

@Entry
@ComponentV2
struct V2MakeObserved {
  @Local observedUser: MakeObservedUser = UIUtils.makeObserved(new MakeObservedUser('Pluto', 64));

  build() {
    Column({ space: 20 }) {

      Child01({ observedUser: this.observedUser })

      Child02({ observedUser: this.observedUser })

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.observedUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@ComponentV2
export struct Child01 {
  @Param observedUser: MakeObservedUser = new MakeObservedUser();

  build() {
    Column() {
      Text('Child01 ' + this.observedUser.name)

      Child03({ observedUser: this.observedUser })
    }
  }
}

@ComponentV2
export struct Child02 {
  @Param observedUser: MakeObservedUser = new MakeObservedUser();

  build() {
    Column() {
      Text('Child02 ' + this.observedUser.age)

      Child04({ observedUser: this.observedUser })
    }
  }
}

@ComponentV2
export struct Child03 {
  @Param observedUser: MakeObservedUser = new MakeObservedUser();

  build() {
    Column() {
      Text('Child03 ' + this.observedUser.name)
    }
  }
}

@ComponentV2
export struct Child04 {
  @Param observedUser: MakeObservedUser = new MakeObservedUser();

  build() {
    Column() {
      Text('Child04 ' + this.observedUser.name)

      Text('Child04 ' + this.observedUser.age)
    }
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // 使用makeObserved方法封装的对象是可被观察的对象
	"reason": "The object data is wrapped by V2's makeObserved",
    // 装饰器信息，可参考@Local使用场景
	"decoratorInfo": [{
        // 使用makeObserved方法获取的decoratorName固定为：MakeObserved
		"decoratorName": "MakeObserved",
		"stateVariableName": "name",
		"owningComponentOrClassName": "MakeObservedUser",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 29,
			"elementName": "Text"
		}, {
			"elementId": 32,
			"elementName": "Text"
		}, {
			"elementId": 37,
			"elementName": "Text"
		}]
	}, {
		"decoratorName": "MakeObserved",
		"stateVariableName": "age",
		"owningComponentOrClassName": "MakeObservedUser",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 34,
			"elementName": "Text"
		}, {
			"elementId": 38,
			"elementName": "Text"
		}]
	}]
}
```

### built-in类型数据使用场景

built-in类型包含：Array、Map、Set、Date类型。

示例代码：

<!-- @[v2_built_in](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V2BuiltIn.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

// 提供判断对象是否为可被观察对象的方法
function test(obj: object): void {
  console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(obj))}`);
}

@Entry
@ComponentV2
struct V2BuiltIn {
  @Local arr: string[] = [];
  @Local map: Map<string, string> = new Map<string, string>();
  @Local set: Set<string> = new Set<string>();
  @Local date: Date = new Date();

  aboutToAppear(): void {
    this.arr = ['1', '2', '3'];
    this.map.set('a', '11');
    this.map.set('b', '22');
    this.map.set('c', '33');
    this.set.add('111');
    this.set.add('222');
    this.set.add('333');
    this.date = new Date('2025-12-12');
  }

  build() {
    Column({ space: 20 }) {

      Child01({ arr: this.arr })

      Child02({ map: this.map })

      Child03({ set: this.set })

      Child04({ date: this.date })

      Button('test arr')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          test(this.arr);
        })

      Button('test map')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          test(this.map);
        })

      Button('test set')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          test(this.set);
        })

      Button('test date')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          test(this.date);
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@ComponentV2
export struct Child01 {
  @Param arr: string[] = [];

  build() {
    Column() {
      ForEach(this.arr, (item: string) => {
        Text('Child01 ' + item)
      })
    }
  }
}

@ComponentV2
export struct Child02 {
  @Param map: Map<string, string> = new Map<string, string>();

  build() {
    Column() {
      ForEach(Array.from(this.map), (item: object) => {
        Text('Child02 ' + JSON.stringify(item))
      })
    }
  }
}

@ComponentV2
export struct Child03 {
  @Param set: Set<string> = new Set<string>();

  build() {
    Column() {
      ForEach(Array.from(this.set), (item: string) => {
        Text('Child03 ' + item)
      })
    }
  }
}

@ComponentV2
export struct Child04 {
  @Param date: Date = new Date();

  build() {
    Column() {
      Text('Child03 year: ' + this.date.getFullYear())
      Text('Child03 month: ' + this.date.getMonth())
      Text('Child03 day: ' + this.date.getDate())
    }
  }
}
```

返回结果：

``` json
// Array结果：
{
    // 可被观察
	"isObserved": true,
    // built-in类型对象是可被观察的对象
	"reason": "The object data is built-in type proxy data (Array/Map/Set/Date) decorated with @Trace",
    // 装饰器信息
	"decoratorInfo": [{
        // built-in类型decoratorName固定为：ProxyObservedV2
		"decoratorName": "ProxyObservedV2",
        // Array类型按数组下标收集依赖，stateVariableName为下标
		"stateVariableName": "0",
        // built-in类型的owningComponentOrClassName是数据类型
		"owningComponentOrClassName": "Array",
        // V2对象默认返回-1
		"owningComponentId": -1,
        // 组件信息
		"dependentInfo": [{
			"elementId": 42,
			"elementName": "ForEach"
		}]
	}, {
		"decoratorName": "ProxyObservedV2",
        // Array类型按数组下标收集依赖，stateVariableName为下标
		"stateVariableName": "1",
		"owningComponentOrClassName": "Array",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 42,
			"elementName": "ForEach"
		}]
	}, {
		"decoratorName": "ProxyObservedV2",
        // Array类型按数组下标收集依赖，stateVariableName为下标
		"stateVariableName": "2",
		"owningComponentOrClassName": "Array",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 42,
			"elementName": "ForEach"
		}]
	}, {
		"decoratorName": "ProxyObservedV2",
        // Array类型收集Array的length属性依赖，stateVariableName为___obj_length
		"stateVariableName": "___obj_length",
		"owningComponentOrClassName": "Array",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 29,
			"elementName": "Child01"
		}, {
			"elementId": 42,
			"elementName": "ForEach"
		}]
	}]
}

// Map结果：
{
	"isObserved": true,
	"reason": "The object data is built-in type proxy data (Array/Map/Set/Date) decorated with @Trace",
	"decoratorInfo": [{
		"decoratorName": "ProxyObservedV2",
        // Map类型收集Map的size属性依赖，stateVariableName为___obj_length
		"stateVariableName": "___obj_length",
		"owningComponentOrClassName": "Map",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 30,
			"elementName": "Child02"
		}, {
			"elementId": 50,
			"elementName": "ForEach"
		}]
	}, {
		"decoratorName": "ProxyObservedV2",
        // Map类型收集Map对象本身的依赖，stateVariableName为___ob_map_set
		"stateVariableName": "___ob_map_set",
		"owningComponentOrClassName": "Map",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 50,
			"elementName": "ForEach"
		}]
	}]
}

// Set结果：
{
	"isObserved": true,
	"reason": "The object data is built-in type proxy data (Array/Map/Set/Date) decorated with @Trace",
	"decoratorInfo": [{
		"decoratorName": "ProxyObservedV2",
        // Set类型收集Set的size属性依赖，stateVariableName为___obj_length
		"stateVariableName": "___obj_length",
		"owningComponentOrClassName": "Set",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 31,
			"elementName": "Child03"
		}, {
			"elementId": 58,
			"elementName": "ForEach"
		}]
	}, {
		"decoratorName": "ProxyObservedV2",
        // Set类型收集Set对象本身的依赖，stateVariableName为___ob_map_set
		"stateVariableName": "___ob_map_set",
		"owningComponentOrClassName": "Set",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 58,
			"elementName": "ForEach"
		}]
	}]
}

// Date结果：
{
	"isObserved": true,
	"reason": "The object data is built-in type proxy data (Array/Map/Set/Date) decorated with @Trace",
	"decoratorInfo": [{
		"decoratorName": "ProxyObservedV2",
        // Date类型收集依赖，stateVariableName为__date__
		"stateVariableName": "__date__",
		"owningComponentOrClassName": "Date",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 66,
			"elementName": "Text"
		}, {
			"elementId": 67,
			"elementName": "Text"
		}, {
			"elementId": 68,
			"elementName": "Text"
		}]
	}]
}
```

## V1调V2组件使用场景

### enableV2Compatibility使用场景

在V1组件中使用[enableV2Compatibility](./arkts-v1-v2-mixusage.md#enablev2compatibility)方法封装的对象，可在V1和V2组件中收集到对象关联的系统组件，V2无法收集自定义组件，V1根据使用的装饰器收集对象关联的组件。

代码示例：

<!-- @[v1_and_v2_compatibility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1AndV2Compatibility.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class CompatibilityUser {
  public name?: string;
  public age?: number;

  constructor(name?: string, age?: number) {
    this.name = name ?? '';
    this.age = age ?? 0;
  }

  // 在对象中提供判断该对象是否为可被观察对象的方法
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

@Entry
@Component
struct V1AndV2Compatibility {
  // 被enableV2Compatibility转换的V1对象必须是可被观察的V1对象
  @State temp: CompatibilityUser = new CompatibilityUser('Galen', 43);
  @State compatibilityUser: CompatibilityUser = UIUtils.enableV2Compatibility(this.temp);

  build() {
    Column({ space: 20 }) {

      Child01({ compatibilityUser: this.compatibilityUser })

      Child02({ compatibilityUser: this.compatibilityUser })

      Button('test')
        .onClick(() => {
          // 开发者可以在任意页面中使用接口来判断当前对象是否为可被观察对象
          this.compatibilityUser.test();
        })

    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
export struct Child01 {
  @State compatibilityUser: CompatibilityUser = new CompatibilityUser();

  build() {
    Column() {
      Text('Child01 ' + this.compatibilityUser.name)
    }
  }
}

@ComponentV2
export struct Child02 {
  @Param compatibilityUser: CompatibilityUser = new CompatibilityUser();

  build() {
    Column() {
      Text('Child02 ' + this.compatibilityUser.age)

      Child03({ compatibilityUser: this.compatibilityUser })
    }
  }
}

@ComponentV2
export struct Child03 {
  @Param compatibilityUser: CompatibilityUser = new CompatibilityUser();

  build() {
    Column() {
      Text('Child03 ' + this.compatibilityUser.name)
    }
  }
}
```

返回结果：

``` json
{
    // 可被观察
	"isObserved": true,
    // 使用enableV2Compatibility方法的V1对象必须可被观察的对象
	"reason": "The V1 Observed object data is wrapped by enableV2Compatibility and used in @ComponentV2",
    // 组件信息
	"decoratorInfo": [{
        // 按照V1的规格收集组件信息
		"decoratorName": "@State",
		"stateVariableName": "temp",
		"owningComponentOrClassName": "V1AndV2Compatibility",
		"owningComponentId": 17,
		"dependentInfo": []
	}, {
		"decoratorName": "@State",
		"stateVariableName": "compatibilityUser",
		"owningComponentOrClassName": "V1AndV2Compatibility",
		"owningComponentId": 17,
		"dependentInfo": [{
			"elementName": "Child01",
			"elementId": 19
		}, {
			"elementName": "Child02",
			"elementId": 20
		}]
	}, {
		"decoratorName": "@State",
		"stateVariableName": "compatibilityUser",
		"owningComponentOrClassName": "Child01",
		"owningComponentId": 19,
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 24
		}]
	}, {
        // 按照V2的规格收集组件信息，使用enableV2Compatibility方法传入V2组件获取的decoratorName固定为：EnableV2Compatible
		"decoratorName": "EnableV2Compatible",
		"stateVariableName": "age",
		"owningComponentOrClassName": "CompatibilityUser",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 26,
			"elementName": "Text"
		}]
	}, {
		"decoratorName": "EnableV2Compatible",
		"stateVariableName": "name",
		"owningComponentOrClassName": "CompatibilityUser",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 29,
			"elementName": "Text"
		}]
	}]
}
```