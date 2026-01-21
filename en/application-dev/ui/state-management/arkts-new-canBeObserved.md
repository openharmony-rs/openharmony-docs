# canBeObserved API: Determining Whether an Object Can Be Observed
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

During development and debugging, you may find that the UI page is not refreshed after the value of an object is modified. This problem is inconvenient in complex services. To solve this problem, the [canBeObserved](../../reference/apis-arkui/js-apis-stateManagement.md#canbeobserved23) API is provided. You can use this API to determine whether an object is observable and obtain the information about the component associated with the object.

>**NOTE**
>
>Since API version 23, you can use the canBeObserved API in UIUtils to determine whether a data object is an observable object.

## V1 Application Scenarios

The application scenarios of V1 include @State, @Link, @Prop, @ObjectLink, @StorageLink, @LocalStorageLink, @StorageProp, @LocalStorageProp, @Provide, @Consume decorator, and makeV1Observed.

### @State Application Scenario

The [@State](./arkts-state.md) decorator can collect system components and custom components associated with objects.

The sample code is as follows:

<!-- @[v1_state](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1State.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class StateUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // Reason for being observable. The object decorated by @State is an observable object.
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // Decorator information
	"decoratorInfo": [{
        // Decorator name.
		"decoratorName": "@State",
        // Attribute name of the decorator.
		"stateVariableName": "stateUser",
        // Name of the component where the decorator is located.
		"owningComponentOrClassName": "V1State",
        // ID of the component where the decorator is located.
		"owningComponentId": 62,
        // Component information associated with the object. @State can collect custom components and system components.
		"dependentInfo": [{
          // Name of the component associated with the object
			"elementName": "Child01",
          // ID of the component associated with the object
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

### @Prop Application Scenario

The [@Prop](./arkts-prop.md) decorator can collect system components and custom components associated with objects.

The sample code is as follows:

<!-- @[v1_prop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1Prop.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class PropUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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

      // Child03 is a child component of Child01. When @Prop is used, the deep copy object is changed and cannot be collected.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // The object decorated by @State is an observable object.
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // Decorator information. The first decorator collects the @State of the parent component. For details, see the @State application scenario.
	"decoratorInfo": [{
		"decoratorName": "@State",
		"stateVariableName": "propUser",
		"owningComponentOrClassName": "V1Prop",  
		"owningComponentId": 62,
        // Component information associated with the object. @State can collect custom components and system components. Child03 is a child component of Child01. When @Prop is used, the deep copy object changes. Therefore, the information cannot be collected.
		"dependentInfo": [{
			"elementName": "Child01",
			"elementId": 64
		}, {
			"elementName": "Child02",
			"elementId": 65
		}]
	}, {
        // Decorator name.
		"decoratorName": "@Prop",
        // Attribute name of the decorator.
		"stateVariableName": "propUser",
        // Name of the component where the decorator is located.
		"owningComponentOrClassName": "Child01",
        // ID of the component where the decorator is located.
		"owningComponentId": 64,
        // Component information associated with the object. @Prop can collect custom components and system components.
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

### @Link Application Scenarios

[@Link](./arkts-link.md) The decorator can collect system components associated with objects, but cannot collect custom components.

The sample code is as follows:

<!-- @[v1_link](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1Link.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class LinkUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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
      // Only the custom component is called, and the component information cannot be collected.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // The object decorated by @State is an observable object.
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // Decorator information. The first decorator collects the @State of the parent component. For details, see the @State application scenario.
	"decoratorInfo": [{
		"decoratorName": "@State",
		"stateVariableName": "linkUser",
		"owningComponentOrClassName": "V1Link",
		"owningComponentId": 62,
        // When @Link is used in the customized subcomponent, it cannot be collected.
		"dependentInfo": []
	}, {
        // Decorator name.
		"decoratorName": "@Link",
        // Name of the attribute decorated by the decorator.
		"stateVariableName": "linkUser",
        // Name of the component where the decorator is located.
		"owningComponentOrClassName": "Child01",
        // ID of the component where the decorator is located.
		"owningComponentId": 64,
        // The @Link decorator can collect only system components and cannot collect custom components.
		"dependentInfo": []
	}, {
		"decoratorName": "@Link",
		"stateVariableName": "linkUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 69,
        // The @Link decorator can collect only system components and cannot collect custom components.
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 71
		}]
	}, {
		"decoratorName": "@Link",
		"stateVariableName": "linkUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
        // The @Link decorator can collect only system components and cannot collect custom components.
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 73
		}]
	}]
}
```

### @ObjectLink Application Scenarios

The [@ObjectLink](./arkts-observed-and-objectlink.md) can collect the system components and custom components associated with the object.

The sample code is as follows:

<!-- @[v1_object_link](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1ObjectLink.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class ObjectLinkUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // The object decorated by @State is an observable object.
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // Decorator information. The first decorator collects the @State of the parent component. For details, see the @State application scenario.
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
        // Decorator name.
		"decoratorName": "@ObjectLink",
        // Name of the attribute decorated by the decorator.
		"stateVariableName": "objLinkUser",
        // Name of the component where the decorator is located.
		"owningComponentOrClassName": "Child01",
        // ID of the component where the decorator is located.
		"owningComponentId": 64,
        // Component information associated with the object. @ObjectLink can collect system components and custom components.
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

### @StorageLink Application Scenarios

[@StorageLink](./arkts-appstorage.md#storagelink) can collect system components associated with objects, but cannot collect custom components.

The sample code is as follows:

<!-- @[v1_storage_link](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1StorageLink.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class StorageLinkUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // The object decorated by @StorageLink is an observable object.
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // Decorator information
	"decoratorInfo": [{
        // By default, a @State decorator is added to the alias of the @StorageLink decorator.
		"decoratorName": "@State",
		"stateVariableName": "user",
		"owningComponentOrClassName": "",
		"dependentInfo": []
	}, {
        // Decorator name.
		"decoratorName": "@StorageLink",
        // Name of the attribute decorated by the decorator.
		"stateVariableName": "storageLinkUser",
        // Name of the component where the decorator is located.
		"owningComponentOrClassName": "V1StorageLink",
        // ID of the component where the decorator is located.
		"owningComponentId": 62,
        // The @StorageLink decorator can collect only system components.
		"dependentInfo": []
	}, {
		"decoratorName": "@StorageLink",
		"stateVariableName": "storageLinkUser",
		"owningComponentOrClassName": "Child01",
		"owningComponentId": 64,
        // The @StorageLink decorator can collect only system components.
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 69
		}]
	}, {
		"decoratorName": "@StorageLink",
		"stateVariableName": "storageLinkUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
        // The @StorageLink decorator can collect only system components.
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 74
		}]
	}, {
		"decoratorName": "@StorageLink",
		"stateVariableName": "storageLinkUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 70,
        // The @StorageLink decorator can collect only system components.
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 72
		}]
	}]
}
```

### @StorageProp Application Scenario

[@StorageProp](./arkts-appstorage.md#storageprop) can collect system components associated with objects, but cannot collect custom components.

The sample code is as follows:

<!-- @[v1_storage_prop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1StorageProp.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class StoragePropUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // The object decorated by @StorageLink is an observable object.
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // Decorator information
	"decoratorInfo": [{
        // By default, a @State decorator is added to the alias of the @StorageLink decorator.
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
        // Decorator name.
		"decoratorName": "@StorageProp",
        // Name of the attribute decorated by the decorator.
		"stateVariableName": "storagePropUser",
        // Name of the component where the decorator is located.
		"owningComponentOrClassName": "Child01",
        // ID of the component where the decorator is located.
		"owningComponentId": 64,
        // The @StorageProp decorator can collect only system components.
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 69
		}]
	}, {
		"decoratorName": "@StorageProp",
		"stateVariableName": "storagePropUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
        // The @StorageProp decorator can collect only system components.
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 74
		}]
	}, {
		"decoratorName": "@StorageProp",
		"stateVariableName": "storagePropUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 70,
        // The @StorageProp decorator can collect only system components.
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 72
		}]
	}]
}
```

### @LocalStorageLink Application Scenario

[@LocalStorageLink](./arkts-localstorage.md#localstoragelink) can collect system components associated with objects, but cannot collect custom components.

The sample code is as follows:

<!-- @[v1_local_storage_link](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1LocalStorageLink.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class LocalStorageLinkUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // The object decorated by @LocalStorageLink is an observable object.
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // Decorator information
	"decoratorInfo": [{
        // By default, a @State decorator is added to the alias of the @LocalStorageLink decorator.
		"decoratorName": "@State",
		"stateVariableName": "localLinkUser",
		"owningComponentOrClassName": "",
		"dependentInfo": []
	}, {
        // Decorator name.
		"decoratorName": "@LocalStorageLink",
        // Name of the attribute decorated by the decorator.
		"stateVariableName": "localUser",
        // Name of the component where the decorator is located.
		"owningComponentOrClassName": "V1LocalStorageLink",
        // ID of the component where the decorator is located.
		"owningComponentId": 62,
        // The @LocalStorageLink decorator can collect only system components.
		"dependentInfo": []
	}, {
		"decoratorName": "@LocalStorageLink",
		"stateVariableName": "localUser",
		"owningComponentOrClassName": "Child01",
		"owningComponentId": 64,
        // The @LocalStorageLink decorator can collect only system components.
		"dependentInfo": []
	}, {
		"decoratorName": "@LocalStorageLink",
		"stateVariableName": "localUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
        // The @LocalStorageLink decorator can collect only system components.
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 73
		}]
	}, {
		"decoratorName": "@LocalStorageLink",
		"stateVariableName": "localUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 69,
        // The @LocalStorageLink decorator can collect only system components.
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 71
		}]
	}]
}
```

### @LocalStorageProp Application Scenario

[@LocalStorageProp](./arkts-localstorage.md#localstorageprop) can collect system components associated with objects, but cannot collect custom components.

The sample code is as follows:

<!-- @[v1_local_storage_prop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1LocalStorageProp.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class LocalStoragePropUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // The object decorated by @LocalStorageLink is an observable object.
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // Decorator information
	"decoratorInfo": [{
       // By default, a @State decorator is added to the alias of the @LocalStorageLink decorator.
		"decoratorName": "@State",
		"stateVariableName": "localPropUser",
		"owningComponentOrClassName": "",
		"dependentInfo": []
	}, {
        // Decorator name.
		"decoratorName": "@LocalStorageLink",
        // Name of the attribute decorated by the decorator.
		"stateVariableName": "localStoragePropUser",
        // Name of the component where the decorator is located.
		"owningComponentOrClassName": "V1LocalStorageProp",
        // ID of the component where the decorator is located.
		"owningComponentId": 62,
		"dependentInfo": []
	}, {
		"decoratorName": "@LocalStorageProp",
		"stateVariableName": "localStoragePropUser",
		"owningComponentOrClassName": "Child01",
		"owningComponentId": 64,
        // The @LocalStorageProp decorator can collect only system components.
		"dependentInfo": []
	}, {
		"decoratorName": "@LocalStorageProp",
		"stateVariableName": "localStoragePropUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
        // The @LocalStorageProp decorator can collect only system components.
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 73
		}]
	}, {
		"decoratorName": "@LocalStorageProp",
		"stateVariableName": "localStoragePropUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 69,
        // The @LocalStorageProp decorator can collect only system components.
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 71
		}]
	}]
}
```

### Application Scenarios of @Provide and @Consume

[@Provide](./arkts-provide-and-consume.md) and [@Consume](./arkts-provide-and-consume.md) are used together. Both of them can collect system components associated with objects, but cannot collect custom components.

The sample code is as follows:

<!-- @[v1_provide_and_consume](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1ProvideAndConsume.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class ProvideConsumeUser {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // The object decorated by @Provide is an observable object.
	"reason": "The object data is decorated with @Observed or wrapped by makeV1Observed",
    // Decorator information
	"decoratorInfo": [{
        // Decorator name.
		"decoratorName": "@Provide",
        // Name of the attribute decorated by the decorator.
		"stateVariableName": "pcUser",
        // Name of the component where the decorator is located.
		"owningComponentOrClassName": "V1ProvideAndConsume",
        // ID of the component where the decorator is located
		"owningComponentId": 62,
        // The @Provide decorator can collect only system components.
		"dependentInfo": []
	}, {
		"decoratorName": "@Consume",
		"stateVariableName": "pcUser",
		"owningComponentOrClassName": "Child01",
		"owningComponentId": 64,
        // The @Consume decorator can collect only system components.
		"dependentInfo": []
	}, {
		"decoratorName": "@Consume",
		"stateVariableName": "pcUser",
		"owningComponentOrClassName": "Child02",
		"owningComponentId": 65,
        // The @Consume decorator can collect only system components.
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 73
		}]
	}, {
		"decoratorName": "@Consume",
		"stateVariableName": "pcUser",
		"owningComponentOrClassName": "Child03",
		"owningComponentId": 69,
        // The @Consume decorator can collect only system components.
		"dependentInfo": [{
			"elementName": "Text",
			"elementId": 71
		}]
	}]
}
```

### Built-in Data Type Application Scenarios

The built-in types include Array, Map, Set, and Date.

The sample code is as follows:

<!-- @[v1_built_in](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1BuiltIn.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

// Provide a method for determining whether an object is observable.
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
          // You can use this API on any page to determine whether the current object can be observed.
          test(this.arr);
        })

      Button('test map')
        .onClick(() => {
          // You can use this API on any page to determine whether the current object can be observed.
          test(this.map);
        })

      Button('test set')
        .onClick(() => {
          // You can use this API on any page to determine whether the current object can be observed.
          test(this.set);
        })

      Button('test date')
        .onClick(() => {
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
// Result of the array type. For details, see the application scenario of @State.
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

// Result of the Map type. For details, see the application scenario of @State.
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

// Set result. For details, see the application scenario of @State.
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

// Result of the Date type. For details, see the application scenario of @State.
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

### makeV1Observed Application Scenarios

Object converted using the [makeV1Observed](./arkts-v1-v2-mixusage.md#makev1observed) method. The component associated with the object is collected based on the decorator used by the subcomponent.

The sample code is as follows:

<!-- @[v1_makeV1Observed](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V1MakeV1Observed.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

class ObservedV1User {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
// For details, see the @State application scenario.
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

## V2 Application Scenarios

The application scenarios of V2 include @Local, @Param, @Computed, @Monitor, @Provider, @Consumer decorator, and makeObserved.

The collection method of the V2 decorator is different from that of the V1 decorator. Generally, the V2 decorator is used together with @ObservedV2 and @Trace.
The V2 decorator collects component information based on the @Trace attribute of the object. Examples:

``` TypeScript
// Define a class.
@ObservedV2
class Test {
  @Trace a?: string;
  @Trace b?: string;
  @Trace c?: string;
}
```
``` json
// Analyze the returned result.
{
	"isObserved": true,
	"reason": "The object data is decorated with V2 @ObservedV2 and @Trace",
    // The decorator information is classified based on the attributes decorated by @Trace.
	"decoratorInfo": [{
		"decoratorName": "@Trace",
        // Name of the @Trace attribute in the object
		"stateVariableName": "a",
		"owningComponentOrClassName": "TestClass",
		"owningComponentId": -1,
        // The component information associated with the same @Trace attribute is collected together.
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

### @Local Application Scenarios

[@Local](./arkts-new-local.md) can be initialized only in the current component. Therefore, only the information about the current component can be collected.

The sample code is as follows:

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

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // The object decorated by @ObservedV2 is an observable object.
	"reason": "The object data is decorated with V2 @ObservedV2 and @Trace",
    // Decorator information. The V2 object collects information based on the attributes decorated by @Trace in the object.
	"decoratorInfo": [{
		"decoratorName": "@Trace",
        // Name of the attribute decorated by @Trace.
		"stateVariableName": "name",
        // Class name of the V2 observable object
		"owningComponentOrClassName": "LocalUser",
        // In V2, -1 is returned by default.
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

### @Param Application Scenarios

[@Param](./arkts-new-param.md) can collect system components associated with the object, but cannot collect custom components.

The sample code is as follows:

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

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // The object decorated by ObservedV2 is an observable object.
	"reason": "The object data is decorated with V2 @ObservedV2 and @Trace",
    // Decorator information. For details, see the @Local application scenario.
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

### @Computed Application Scenarios

[@Computed](./arkts-new-computed.md) can collect the @Computed method name and method ID associated with the object.

The sample code is as follows:

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

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // The object decorated by @ObservedV2 is an observable object.
	"reason": "The object data is decorated with V2 @ObservedV2 and @Trace",
    // Decorator information. For details, see the @Local application scenario.
	"decoratorInfo": [{
		"decoratorName": "@Trace",
		"stateVariableName": "name",
		"owningComponentOrClassName": "ComputedUser",
		"owningComponentId": -1,
        // Component information. The V2 decorator can collect the @Computed method name and ID.
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

### @Monitor Application Scenarios

[@Monitor](./arkts-new-monitor.md) can collect the @Monitor method name and method ID associated with the object.

The sample code is as follows:

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

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // The object decorated by @ObservedV2 is an observable object.
	"reason": "The object data is decorated with V2 @ObservedV2 and @Trace",
    // Decorator information. For details, see the @Local application scenario.
	"decoratorInfo": [{
		"decoratorName": "@Trace",
		"stateVariableName": "name",
		"owningComponentOrClassName": "MonitorUser",
		"owningComponentId": -1,
        // Component information. The V2 decorator can collect the @Monitor method name and ID.
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

### @Provider and @Consumer Application Scenarios

[@Provider](./arkts-new-provider-and-consumer.md) and [@Consumer](./arkts-new-provider-and-consumer.md) are used together. Both of them can collect system components associated with objects, but cannot collect custom components.

The sample code is as follows:

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

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // The object decorated by @ObservedV2 is an observable object.
	"reason": "The object data is decorated with V2 @ObservedV2 and @Trace",
    // Decorator information. For details, see the @Local application scenario.
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

### makeObserved Application Scenarios

For objects encapsulated using the [makeObserved](./arkts-new-makeObserved.md) method, system components associated with the objects can be collected, but custom components cannot be collected.

The sample code is as follows:

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

  // Provide a method in the object to determine whether the object can be observed.
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
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // The object encapsulated using the makeObserved method is an observable object.
	"reason": "The object data is wrapped by V2's makeObserved",
    // Decorator information. For details, see the @Local application scenario.
	"decoratorInfo": [{
        // The decoratorName obtained by using the makeObserved method is fixed at MakeObserved.
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

### Built-in Data Type Application Scenarios

The built-in types include Array, Map, Set, and Date.

The sample code is as follows:

<!-- @[v2_built_in](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UIUtilsCanBeObserved/entry/src/main/ets/pages/V2BuiltIn.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

const TAG = 'CanBeObserved';

// Provide a method for determining whether an object is observable.
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
          // You can use this API on any page to determine whether the current object can be observed.
          test(this.arr);
        })

      Button('test map')
        .onClick(() => {
          // You can use this API on any page to determine whether the current object can be observed.
          test(this.map);
        })

      Button('test set')
        .onClick(() => {
          // You can use this API on any page to determine whether the current object can be observed.
          test(this.set);
        })

      Button('test date')
        .onClick(() => {
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
// Array result:
{
    // Observable
	"isObserved": true,
    // Objects of the built-in type are observable objects.
	"reason": "The object data is built-in type proxy data (Array/Map/Set/Date) decorated with @Trace",
    // Decorator information
	"decoratorInfo": [{
        // decoratorName of the built-in type is fixed to ProxyObservedV2.
		"decoratorName": "ProxyObservedV2",
        // For the array type, collect dependencies based on the array subscript. stateVariableName is the subscript.
		"stateVariableName": "0",
        // owningComponentOrClassName of the built-in type is the data type.
		"owningComponentOrClassName": "Array",
        // For a V2 object, -1 is returned by default.
		"owningComponentId": -1,
        // Component information
		"dependentInfo": [{
			"elementId": 42,
			"elementName": "ForEach"
		}]
	}, {
		"decoratorName": "ProxyObservedV2",
        // For the array type, collect dependencies based on the array subscript. stateVariableName is the subscript.
		"stateVariableName": "1",
		"owningComponentOrClassName": "Array",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 42,
			"elementName": "ForEach"
		}]
	}, {
		"decoratorName": "ProxyObservedV2",
        // For the array type, collect dependencies based on the array subscript. stateVariableName is the subscript.
		"stateVariableName": "2",
		"owningComponentOrClassName": "Array",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 42,
			"elementName": "ForEach"
		}]
	}, {
		"decoratorName": "ProxyObservedV2",
        // For the array type, collect the length attribute dependency of the array. stateVariableName is ___obj_length.
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

// Map result:
{
	"isObserved": true,
	"reason": "The object data is built-in type proxy data (Array/Map/Set/Date) decorated with @Trace",
	"decoratorInfo": [{
		"decoratorName": "ProxyObservedV2",
        // For the Map type, collect the size attribute dependency of the Map. The value of stateVariableName is ___obj_length.
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
        // For the Map type, collect the dependency of the Map object. stateVariableName is ___ob_map_set.
		"stateVariableName": "___ob_map_set",
		"owningComponentOrClassName": "Map",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 50,
			"elementName": "ForEach"
		}]
	}]
}

// Set result:
{
	"isObserved": true,
	"reason": "The object data is built-in type proxy data (Array/Map/Set/Date) decorated with @Trace",
	"decoratorInfo": [{
		"decoratorName": "ProxyObservedV2",
        // For the Set type, collect the size attribute dependency of the Set. stateVariableName is ___obj_length.
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
        // For the Set type, collect the dependency of the Set object. stateVariableName is ___ob_map_set.
		"stateVariableName": "___ob_map_set",
		"owningComponentOrClassName": "Set",
		"owningComponentId": -1,
		"dependentInfo": [{
			"elementId": 58,
			"elementName": "ForEach"
		}]
	}]
}

// Date result:
{
	"isObserved": true,
	"reason": "The object data is built-in type proxy data (Array/Map/Set/Date) decorated with @Trace",
	"decoratorInfo": [{
		"decoratorName": "ProxyObservedV2",
        // Date type collection dependency. The value of stateVariableName is __date__.
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

## V1 Invoking V2 Components Application Scenarios

### Application scenarios of enableV2Compatibility

If an object is encapsulated using the [enableV2Compatibility](./arkts-v1-v2-mixusage.md#enablev2compatibility) method in the V1 component, the system components associated with the object can be collected in the V1 and V2 components. The V2 component cannot collect custom components. The V1 component collects the components associated with the object based on the used decorator.

Code example:

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

  // Provide a method in the object to determine whether the object can be observed.
  test(): void {
    console.info(TAG, `res: ${JSON.stringify(UIUtils.canBeObserved(this))}`);
  }
}

@Entry
@Component
struct V1AndV2Compatibility {
  // The V1 object converted by enableV2Compatibility must be observable.
  @State temp: CompatibilityUser = new CompatibilityUser('Galen', 43);
  @State compatibilityUser: CompatibilityUser = UIUtils.enableV2Compatibility(this.temp);

  build() {
    Column({ space: 20 }) {

      Child01({ compatibilityUser: this.compatibilityUser })

      Child02({ compatibilityUser: this.compatibilityUser })

      Button('test')
        .onClick(() => {
          // You can use this API on any page to determine whether the current object can be observed.
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

Returned result:

``` json
{
    // Observable
	"isObserved": true,
    // The V1 object that uses the enableV2Compatibility method must be observable.
	"reason": "The V1 Observed object data is wrapped by enableV2Compatibility and used in @ComponentV2",
    // Component information
	"decoratorInfo": [{
        // Collect component information based on V1 specifications.
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
        // Collect component information based on the V2 specifications. Use the enableV2Compatibility method to pass the V2 component. The decoratorName obtained is fixed to EnableV2Compatible.
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
