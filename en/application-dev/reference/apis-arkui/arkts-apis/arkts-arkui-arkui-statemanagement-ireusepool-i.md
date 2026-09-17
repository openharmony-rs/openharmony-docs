# IReusePool

The **IReusePool** API provides the features related to the global reuse pool of a custom component.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## getReusableInfo

```TypeScript
getReusableInfo(constructor: ReusableComponentConstructor,
    reuseId?: string): IReusableInfo[] | IReusableInfo | undefined
```

Obtains the information about the recycling instance of a given reusable component type in this reuse pool.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| constructor | [ReusableComponentConstructor](arkts-arkui-reusablecomponentconstructor-t.md) | Yes | Name of the reusable custom component to be queried. |
| reuseId | string | No | Reuse ID for filtering. If specified, only the information about the reuse pool with the reuse ID is returned. The default value is **undefined**, indicating that information about all reuse pools is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [IReusableInfo](arkts-arkui-arkui-statemanagement-ireusableinfo-i.md)[] &#124; [IReusableInfo](arkts-arkui-arkui-statemanagement-ireusableinfo-i.md) &#124; undefined | If the reuse pool is not configured to accept the given component type, **undefined** is returned.<br>If **reuseId** is specified, a single **IReusableInfo** is returned (even if **count** is set to **0** and **maxCount** is set to the default value). <br>If **reuseId** is not specified and the reusable component does not use **reuseId**, a single **IReusableInfo** is returned. <br>If **reuseId** is not specified but the reusable component uses **reuseId**, an **Array&lt;IReusableInfo&gt;** is returned, providing a separate entry for each **reuseId** that has a positive value of **count** or a non- default value of **maxCount** as well as an entry of **reuseId: undefined**. |

**Examples**

```TypeScript
import { UIUtils, IReusableInfo } from '@kit.ArkUI';

@ReusableV2
@ComponentV2
struct ReusableChild {
  aboutToRecycle() {
    console.info('ReusableChild aboutToRecycle');
  }
  aboutToReuse() {
    console.info('ReusableChild aboutToReuse');
  }

  build() {
    Text('ReusableChild')
  }
}

@Entry
@ComponentV2({ reusePool: 'perInstance', poolAccepts: [ReusableChild], freezeWhenInactive: false })
struct PoolOwner {
  @Local showChild: boolean = true;

  inspectPool() {
    const pool = UIUtils.getCustomComponentContext(this).getReusePool();
    if (!pool) {
      return;
    }

    // Query the type of components accepted by the pool.
    const info = pool.getReusableInfo(ReusableChild);
    if (info === undefined) {
      console.info('No reuse pool that accepts ReusableChild');
    } else if (Array.isArray(info)) {
      // Multiple reuseId buckets are used.
      info.forEach((item: IReusableInfo, i: number) => {
        console.info(`[${i}] reuseId=${item.reuseId}, count=${item.count}, maxCount=${item.maxCount}`);
      });
    } else {
      // Single entry (reuseId is not used, or a specific reuseId is queried).
      console.info(`count=${info.count}, maxCount=${info.maxCount}`);
    }

    // Query a specific reuseId. A single IReusableInfo is always returned.
    const bucketInfo = pool.getReusableInfo(ReusableChild, 'A') as IReusableInfo;
    console.info(`reuseId 'A': count=${bucketInfo.count}, maxCount=${bucketInfo.maxCount}`);
  }

  build() {
    Column() {
      Button('Switch Child Component')
        .onClick(() => {
          this.showChild = !this.showChild;
        })
      Button('Check Pool')
        .onClick(() => this.inspectPool())
      if (this.showChild) {
        ReusableChild()
          .reuse({ reuseId: () => 'A' })
      }
    }
  }
}
```

## preRender

```TypeScript
preRender(builder: WrappedBuilder<[]>, times: number): Promise<void>
```

Pre-creates @Reusable/@ReusableV2 decorated components and places them in this reuse pool.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [WrappedBuilder](../arkts-components/arkts-arkui-wrappedbuilder-c.md)&lt;[]&gt; | Yes | **WrappedBuilder** that contains the @Builder decorated function to be executed *n* times. Each execution should create one or more @Reusable/@ReusableV2 decorated components. |
| times | number | Yes | Number of times the @Builder decorated function is executed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise parsed when the idle task is successfully completed. This promise returns no value. |

**Examples**

```TypeScript
import { UIUtils, IReusableInfo } from '@kit.ArkUI';

@ReusableV2
@ComponentV2
struct ReusableComponent {
  @Param param: number = 8;

  aboutToAppear() {
    console.info('ReusableComponent aboutToAppear');
  }
  aboutToReuse() {
    console.info('ReusableComponent aboutToReuse');
  }

  build() {
    Column() {
      Text(`ReusableComponent ${this.param}`)
    }
  }
}

@Builder 
function preRenderBuilder() {
  ReusableComponent()
}

@Entry
@ComponentV2({ reusePool: 'shared', poolAccepts: [ReusableComponent], freezeWhenInactive: false })
struct Index {
  @Local onUIFullyLoaded: boolean = false;

  aboutToAppear() {
    // Obtain the pool and schedule pre-rendering.
    const pool = UIUtils.getCustomComponentContext(this).getReusePool();
    // Preload the reusable components in preRenderBuilder to this global reuse pool and execute preRenderBuilder once.
    pool!.preRender(new WrappedBuilder<[]>(preRenderBuilder), 1)
      .then(() => {
        console.info('ReusableComponent preRender completes');
      });
  }

  checkPool() {
    // Obtain the number of components in the global reuse pool.
    const reusePool = UIUtils.getCustomComponentContext(this).getReusePool();
    const reusableInfo: IReusableInfo = reusePool!.getReusableInfo(ReusableComponent) as IReusableInfo;
    console.info(`ReusableComponent reuse pool count=${reusableInfo.count}`);
  }

  build() {
    Column({ space: 5 }) {
      Button('Switch')
        .onClick(() => {
          this.onUIFullyLoaded = !this.onUIFullyLoaded;
        })
        .width(100)
      Button('Check pool')
        .onClick(() => {
          this.checkPool();
        })
        .width(100)
      CompA({ showFullUI: this.onUIFullyLoaded })
    }
    .width('100%')
  }
}

@ComponentV2
struct CompA {
  @Require @Param showFullUI: boolean;

  build() {
    if (this.showFullUI) {
      // This will reuse the pre-rendered instance from the pool.
      ReusableComponent()
    }
  }
}
```
