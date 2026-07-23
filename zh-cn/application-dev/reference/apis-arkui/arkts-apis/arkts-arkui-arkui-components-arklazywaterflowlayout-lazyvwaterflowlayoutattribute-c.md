# LazyVWaterFlowLayoutAttribute

定义懒加载垂直瀑布流布局属性。

**继承/实现关系：** LazyVWaterFlowLayoutAttribute extends [LazyWaterFlowLayoutAttribute<LazyVWaterFlowLayoutAttribute>]

**起始版本：** 26.0.0

<!--Device-unnamed-export declare class LazyVWaterFlowLayoutAttribute extends LazyWaterFlowLayoutAttribute<LazyVWaterFlowLayoutAttribute>--><!--Device-unnamed-export declare class LazyVWaterFlowLayoutAttribute extends LazyWaterFlowLayoutAttribute<LazyVWaterFlowLayoutAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { LazyVWaterFlowLayout, LazyWaterFlowLayoutAttribute, LazyVWaterFlowLayoutAttribute } from '@kit.ArkUI';
```

## columnsTemplate

```TypeScript
columnsTemplate(value: string | ItemFillPolicy | undefined): LazyVWaterFlowLayoutAttribute
```

该参数用于指定当前瀑布流布局中的列数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyVWaterFlowLayoutAttribute-columnsTemplate(value: string | ItemFillPolicy | undefined): LazyVWaterFlowLayoutAttribute--><!--Device-LazyVWaterFlowLayoutAttribute-columnsTemplate(value: string | ItemFillPolicy | undefined): LazyVWaterFlowLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| ItemFillPolicy \| undefined | 是 | 布局中的列数。<br>默认值：'1fr' |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LazyVWaterFlowLayoutAttribute](arkts-arkui-arkui-components-arklazywaterflowlayout-lazyvwaterflowlayoutattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

