# IReusePool

`IReusePool`接口提供自定义组件上的全局复用池的相关功能，包括查询回收组件的当前数量和上限信息、预渲染可复用组件到复用池中等，适用于开发者需要手动管理和优化组件复用效率的场景。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo } from '@kit.ArkUI';
```

## getReusableInfo

```TypeScript
getReusableInfo(constructor: ReusableComponentConstructor,
    reuseId?: string): IReusableInfo[] | IReusableInfo | undefined
```

检索此复用池中给定可复用组件类型的回收实例信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| constructor | [ReusableComponentConstructor](arkts-arkui-reusablecomponentconstructor-t.md) | 是 | 要查询的可复用自定义组件的构造函数。 |
| reuseId | string | 否 | 可选的reuseId用于过滤结果。如果指定，则仅返回此特定reuseId复用池的信息。默认值是undefined，返回所有reuseId复用池信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IReusableInfo](arkts-arkui-arkui-statemanagement-ireusableinfo-i.md)[] \| [IReusableInfo](arkts-arkui-arkui-statemanagement-ireusableinfo-i.md) \| undefined | 如果此复用池未配置为接受给定的组件类型，则返回`undefined`。 |

**示例**

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

    // 查询池接受的组件类型。
    const info = pool.getReusableInfo(ReusableChild);
    if (info === undefined) {
      console.info('No reuse pool that accepts ReusableChild');
    } else if (Array.isArray(info)) {
      // 使用了多个 reuseId 桶。
      info.forEach((item: IReusableInfo, i: number) => {
        console.info(`[${i}] reuseId=${item.reuseId}, count=${item.count}, maxCount=${item.maxCount}`);
      });
    } else {
      // 单个条目（未使用 reuseId，或查询了特定的 reuseId）。
      console.info(`count=${info.count}, maxCount=${info.maxCount}`);
    }

    // 查询特定的 reuseId — 始终返回单个 IReusableInfo。
    const bucketInfo = pool.getReusableInfo(ReusableChild, 'A') as IReusableInfo;
    console.info(`reuseId 'A': count=${bucketInfo.count}, maxCount=${bucketInfo.maxCount}`);
  }

  build() {
    Column() {
      Button('切换子组件')
        .onClick(() => {
          this.showChild = !this.showChild;
        })
      Button('检查池')
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

调用空闲任务以预创建可复用组件并在首次使用前将其放入复用池。

> **说明：**
> 
> 1. `preRender`仅将池配置为接受的组件放入池中。预渲染池不接受的组件会立即创建并销毁。
> 
> 2. 预渲染期间不会从池中复用组件；池仅接受新创建的实例。
> 
> 3. @Builder函数执行完整的深度渲染，包括嵌套的子组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | [WrappedBuilder](../arkts-components/arkts-arkui-wrappedbuilder-c.md)&lt;[]&gt; | 是 | 包含要执行`times`次的@Builder函数的 `WrappedBuilder`。每次执行应创建一个或多个 [@Reusable](../../../ui/state-management/arkts-create-custom-components.md#reusable)/ [@ReusableV2](../../../ui/state-management/arkts-create-custom-components.md#reusablev2)组件。 |
| times | number | 是 | 执行@Builder函数的次数。取值范围为正整数。传入0或负数时不生效。传入小数时会向上取整。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 当空闲任务成功完成时兑现的Promise。Promise对象无返回结果。当预渲染任务执行失败时，Promise会被拒绝。 |

**示例**

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
    // 获取池并调度预渲染。
    const pool = UIUtils.getCustomComponentContext(this).getReusePool();
    // 预加载preRenderBuilder内的复用组件到当前的全局复用池中，执行一次preRenderBuilder。
    pool!.preRender(new WrappedBuilder<[]>(preRenderBuilder), 1)
      .then(() => {
        console.info('ReusableComponent preRender completes');
      });
  }

  checkPool() {
    // 获取全局复用池内组件数量
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
      // 这将从池中复用预渲染的实例。
      ReusableComponent()
    }
  }
}
```
