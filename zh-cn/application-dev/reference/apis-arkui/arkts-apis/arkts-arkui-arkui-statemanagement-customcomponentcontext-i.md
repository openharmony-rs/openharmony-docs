# CustomComponentContext

```TypeScript
export declare interface CustomComponentContext
```

`CustomComponentContext`类提供对组件级服务的访问，包括复用池。通过[UIUtils.getCustomComponentContext](arkts-arkui-arkui-statemanagement-uiutils-c.md#getcustomcomponentcontext)获取实例。

**起始版本：** 26.0.0

<!--Device-unnamed-export declare interface CustomComponentContext--><!--Device-unnamed-export declare interface CustomComponentContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IDefaultReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo, RecoverableStorage, RecoverableConnectOptions, RecoverableStorageError, NotifyOnErrorCallback } from '@kit.ArkUI';
```

## getDefaultReusePool

```TypeScript
getDefaultReusePool(): IDefaultReusePool | undefined
```

返回该自定义组件拥有的默认复用池。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-CustomComponentContext-getDefaultReusePool(): IDefaultReusePool | undefined--><!--Device-CustomComponentContext-getDefaultReusePool(): IDefaultReusePool | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IDefaultReusePool](arkts-arkui-arkui-statemanagement-idefaultreusepool-i.md) &#124; undefined | 当前组件存在默认复用池时，返回默认复用池，否则返回`undefined`。 |

**示例**

以下示例中，点击Recycle child按钮可将自定义组件回收进默认复用池，点击Clear按钮可释放默认复用池中的组件。

```TypeScript
import { UIUtils } from '@kit.ArkUI';

@ReusableV2
@ComponentV2
struct ReusableChild {
  @Param label: string = '';
  aboutToAppear() {
    console.info(`ReusableChild [${this.label}] aboutToAppear`);
  }
  aboutToDisappear() {
    console.info(`ReusableChild [${this.label}] aboutToDisappear`);
  }
  aboutToRecycle() {
    console.info(`ReusableChild [${this.label}] aboutToRecycle`);
  }
  aboutToReuse() {
    console.info(`ReusableChild [${this.label}] aboutToReuse`);
  }

  build() {
    Text(`ReusableChild: ${this.label}`)
  }
}

@Entry
@ComponentV2
struct Index {
  @Local showChild: boolean = true;

  clearDefaultPool() {
    // 获取当前组件的默认复用池
    const pool = UIUtils.getCustomComponentContext(this).getDefaultReusePool?.();
    if (!pool) {
      console.info('No default reuse pool available.');
      return;
    }
    // 清理默认复用池中的全部组件
    pool.clearCache();
    // 也可以仅清理reuseId为'A'的组件
    // pool.clearCache('A');
  }

  build() {
    Column() {
      if (this.showChild) {
        ReusableChild({ label: 'A' })
          .reuse({ reuseId: () => 'A' })
      }
      Button('Recycle child')
        .onClick(() => {
          // 切换if分支，触发子组件回收
          this.showChild = false;
        })
      Button('Clear')
        .onClick(() => {
          // 主动清理复用池
          this.clearDefaultPool();
        })
    }
  }
}
```

## getReusePool

```TypeScript
getReusePool(): IReusePool | undefined
```

返回该自定义组件拥有的全局复用池。如果组件或其上层组件没有通过`reusePool`和`poolAccepts`配置全局复用池，则返回`undefined`。配置全局复用池方式请参考[全局复用开发指南](../../../ui/state-management/arkts-global-reuse-pool.md)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-CustomComponentContext-getReusePool(): IReusePool | undefined--><!--Device-CustomComponentContext-getReusePool(): IReusePool | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IReusePool](arkts-arkui-arkui-statemanagement-ireusepool-i.md) &#124; undefined | 当前组件配置全局复用池时，返回复用池信息，否则返回`undefined`。 |

**示例**

```TypeScript
import { UIUtils } from '@kit.ArkUI';

@ReusableV2
@ComponentV2
struct ReusableChild {
  build() {
    Text('ReusableChild')
  }
}

@Entry
@ComponentV2({ reusePool: 'perInstance', poolAccepts: [ReusableChild], freezeWhenInactive: false })
struct PoolOwner {
  checkPool() {
    const pool = UIUtils.getCustomComponentContext(this).getReusePool();
    if (pool) {
      console.info('Global reuse pool configured.');
    } else {
      console.info('No global reuse pool configured.');
    }
  }

  build() {
    Column() {
      ReusableChild()
      Button('Check Pool')
        .onClick(() => {
          this.checkPool();
        })
    }
  }
}
```
