# IReusePool

```TypeScript
export declare interface IReusePool
```

Provides the features related to the global reuse pool of a custom component, including querying the current count and upper limit of recycled components and pre-rendering reusable components into the reuse pool. It is suitable for scenarios where you need to manually manage and optimize component reuse efficiency.

**Since:** 26.0.0

<!--Device-unnamed-export declare interface IReusePool--><!--Device-unnamed-export declare interface IReusePool-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## getReusableInfo

```TypeScript
getReusableInfo(constructor: ReusableComponentConstructor,
    reuseId?: string): IReusableInfo[]  | IReusableInfo | undefined
```

Obtains the information about the recycling instance of a given reusable component type in this reuse pool.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-IReusePool-getReusableInfo(constructor: ReusableComponentConstructor,    reuseId?: string): IReusableInfo[] | IReusableInfo | undefined--><!--Device-IReusePool-getReusableInfo(constructor: ReusableComponentConstructor,    reuseId?: string): IReusableInfo[] | IReusableInfo | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| constructor | [ReusableComponentConstructor](arkts-arkui-reusablecomponentconstructor-t.md) | Yes | Constructor of the reusable custom component to be queried. |
| reuseId | string | No | Reuse ID for filtering. If specified, only the information about the reuse pool with the reuse ID is returned. The default value is **undefined**, indicating that information about all reuse pools is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [IReusableInfo](arkts-arkui-arkui-statemanagement-ireusableinfo-i.md)[] &#124; [IReusableInfo](arkts-arkui-arkui-statemanagement-ireusableinfo-i.md) &#124; undefined | If the reuse pool is not configured to accept the given component type, **undefined** is returned.<br>If **reuseId** is specified, a single **IReusableInfo** is returned (even if **count** is set to **0** and **maxCount** is set to the default value). <br>If the **reuseId** parameter is not specified and the reusable component is created without a reuse ID, a single **IReusableInfo** is returned. <br>If the **reuseId** parameter is not specified but the reusable component is created with a reuse ID, an **Array&lt;IReusableInfo&gt;** is returned, providing a separate entry for each reuse ID with a positive count or a non-default **maxCount**, plus an entry of **reuseId: undefined**. |

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

Invokes an idle task to pre-create a reusable component and put it into the reuse pool before it is used for the first time.

> **NOTE:** 
> 
> 1. **preRender** only places components that are configured to be accepted by the pool into the pool. Components that are not accepted by the pre-rendering pool are created and destroyed immediately.
> 
> 2. During pre-rendering, components are not reused from the pool. The pool only accepts newly created instances.
> 
> 3. The **@Builder** decorated function performs complete deep rendering, including nested child components.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-IReusePool-preRender(builder: WrappedBuilder<[]>, times: number): Promise<void>--><!--Device-IReusePool-preRender(builder: WrappedBuilder<[]>, times: number): Promise<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [WrappedBuilder](../arkts-components/arkts-arkui-common-comp-wrappedbuilder-c.md)&lt;[]&gt; | Yes | **WrappedBuilder** that contains the \@Builder decorated function to be executed *times* times. One or more [\@Reusable](../../../ui/state-management/arkts-create-custom-components.md#reusable)/[\@ReusableV2](../../../ui/state-management/arkts-create-custom-components.md#reusablev2) components should be created for each execution. |
| times | number | Yes | Number of times the \@Builder decorated function is executed. The value is a positive integer. If 0 or a negative number is passed, the value does not take effect. If a decimal is passed, it is rounded up. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that is fulfilled when the idle task completes successfully. This promise returns no value. If the pre-rendering task fails to be executed, the promise will be rejected. |

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
