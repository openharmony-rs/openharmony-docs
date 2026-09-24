# LazyVWaterFlowLayout属性/事件

```TypeScript
export declare class LazyVWaterFlowLayoutAttribute extends LazyWaterFlowLayoutAttribute<LazyVWaterFlowLayoutAttribute>
```

定义懒加载垂直瀑布流布局属性。

@extends LazyWaterFlowLayoutAttribute&lt;LazyVWaterFlowLayoutAttribute&gt;

**继承/实现关系：** LazyVWaterFlowLayoutAttribute extends LazyWaterFlowLayoutAttribute<LazyVWaterFlowLayoutAttribute>

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { LazyVWaterFlowLayout, LazyVWaterFlowLayoutAttribute, LazyWaterFlowLayoutAttribute } from '@kit.ArkUI';
```

## columnsTemplate

```TypeScript
columnsTemplate(value: string | ItemFillPolicy | undefined)
```

该参数用于指定当前瀑布流布局中的列数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string &#124; [ItemFillPolicy](../arkts-apis/arkts-arkui-itemfillpolicy-i.md) &#124; undefined | 是 | 布局中的列数。<br>默认值：'1fr'<br>非repeat形式的模板串中每项仅支持'数字+fr'、'数字+px'、'数字+%'三种格式，不支持vp（如columnsTemplate('100vp 100vp')）<br>设置为'0fr'时，该列的列宽为0，不显示子组件；设置为其他非法值时，子组件显示为固定1列 |
