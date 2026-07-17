# CustomComponentContext

`CustomComponentContext`类提供对组件级服务的访问，包括复用池。通过[UIUtils.getCustomComponentContext](arkts-arkui-arkui-statemanagement-uiutils-c.md#getcustomcomponentcontext-1)获取实例。

**起始版本：** 26.0.0

<!--Device-unnamed-export declare interface CustomComponentContext--><!--Device-unnamed-export declare interface CustomComponentContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Binding, ComponentReuse, CustomComponentLifecycleState, ComponentInactive, PersistenceV2, ComponentDisappear, MutableBinding, CustomComponentLifecycleObserver, AppStorageV2, Type, ConnectOptionsCollections, CollectionType, CustomComponentContext, IReusePool, ConnectOptions, UIUtils, ComponentActive, CustomComponentLifecycle, ComponentInit, ComponentAppear, ComponentBuilt, ComponentRecycle, IReusableInfo } from '@kit.ArkUI';
```

## getReusePool

```TypeScript
getReusePool(): IReusePool | undefined
```

返回该自定义组件拥有的全局复用池。如果组件没有通过`reusePool`和`poolAccepts`配置复用池，则返回`undefined`。配置全局复用池方式请参考[全局复用开发指南](../../../../ui/state-management/arkts-global-reuse-pool.md)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentContext-getReusePool(): IReusePool | undefined--><!--Device-CustomComponentContext-getReusePool(): IReusePool | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IReusePool](arkts-arkui-arkui-statemanagement-ireusepool-i.md) | If a global reuse pool is configured for the current component, the reuse pool information is returned. Otherwise, **undefined** is returned. |

**示例：**

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

