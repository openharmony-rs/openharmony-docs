# CustomComponentContext

\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_类提供对组件级服务的访问，包括复用池。通过 [UIUtils.getCustomComponentContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_获取实例。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

<!--Device-unnamed-export declare interface CustomComponentContext--><!--Device-unnamed-export declare interface CustomComponentContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getReusePool

```TypeScript
getReusePool(): IReusePool | undefined
```

返回该自定义组件拥有的全局复用池。如果组件或其上层组件没有通过\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_和\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_配置全局复用池，则返回\_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_。配置全局复用池方式请参考 \_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentContext-getReusePool(): IReusePool | undefined--><!--Device-CustomComponentContext-getReusePool(): IReusePool | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 当前组件配置全局复用池时，返回复用池信息，否则返回\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

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

