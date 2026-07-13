# CustomComponentContext

`CustomComponentContext`类提供对组件级服务的访问，包括复用池。通过
[UIUtils.getCustomComponentContext](arkts-arkui-uiutils-c.md#getcustomcomponentcontext-1)获取实例。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getReusePool

```TypeScript
getReusePool(): IReusePool | undefined
```

返回该自定义组件拥有的全局复用池。如果组件没有通过`reusePool`和`poolAccepts`配置复用池，则返回`undefined`。配置全局复用池方式请参考
[全局复用开发指南](../../../../ui/state-management/arkts-global-reuse-pool.md)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IReusePool | If a global reuse pool is configured for the current component, the reuse poolinformation is returned. Otherwise, **undefined** is returned. |

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

