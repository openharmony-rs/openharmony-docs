# LazyDynamicLayout

## 导入模块

```TypeScript
import { LazyDynamicLayoutAttribute, LazyDynamicLayout } from '@kit.ArkUI';
```

## LazyDynamicLayout

```TypeScript
export declare function LazyDynamicLayout(algorithm: LazyLayoutAlgorithm): LazyDynamicLayoutAttribute
```

定义LazyDynamicLayout组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare function LazyDynamicLayout(algorithm: LazyLayoutAlgorithm): LazyDynamicLayoutAttribute--><!--Device-unnamed-export declare function LazyDynamicLayout(algorithm: LazyLayoutAlgorithm): LazyDynamicLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algorithm | [LazyLayoutAlgorithm](arkts-arkui-lazylayoutalgorithm-i.md) | 是 | Lazy layout algorithm. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LazyDynamicLayoutAttribute](arkts-arkui-arkui-components-arklazydynamiclayout-lazydynamiclayoutattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

