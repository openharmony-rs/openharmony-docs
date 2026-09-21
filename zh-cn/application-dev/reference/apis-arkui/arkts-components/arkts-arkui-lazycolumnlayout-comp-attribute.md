# LazyColumnLayout属性/事件

```TypeScript
export declare class LazyColumnLayoutAttribute extends CommonMethod<LazyColumnLayoutAttribute>
```

定义懒加载列布局属性。

@extends CommonMethod&lt;LazyColumnLayoutAttribute&gt;

**继承/实现关系：** LazyColumnLayoutAttribute extends CommonMethod<LazyColumnLayoutAttribute>

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { LazyColumnLayout, LazyColumnLayoutAttribute } from '@kit.ArkUI';
```

## alignItems

```TypeScript
alignItems(value: HorizontalAlign | undefined)
```

设置行内容的水平对齐方式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [HorizontalAlign](../arkts-apis/arkts-arkui-horizontalalign-e.md) &#124; undefined | 是 | 行内容的水平对齐。<br>默认值为HorizontalAlign.Center。 |

## footer

```TypeScript
footer(builder: CustomBuilder | undefined)
```

设置懒加载列布局的footer。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; undefined | 是 | footer生成器函数<br>传入undefined移除footer。 |

## header

```TypeScript
header(builder: CustomBuilder | undefined)
```

设置懒加载列布局的header。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; undefined | 是 | header生成器函数<br>传递undefined将移除header。 |

## onVisibleIndexesChange

```TypeScript
onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined)
```

当子组件在可见区域的索引发生变化时触发。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnVisibleIndexesChangeCallback](arkts-arkui-common-comp-onvisibleindexeschangecallback-t.md) &#124; undefined | 是 | 回调函数，当可见区域中子组件的索引发生变化时触发。<br>传递undefined将取消注册回调。 |

## space

```TypeScript
space(space: LengthMetrics | undefined)
```

行之间的间距。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| space | LengthMetrics &#124; undefined | 是 | 行之间的间距。<br>默认值为0。<br>范围：[0, +∞)。 |

## sticky

```TypeScript
sticky(sticky: StickyStyle | undefined)
```

设置header和footer吸顶吸底样式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sticky | [StickyStyle](arkts-arkui-list-comp-stickystyle-e.md) &#124; undefined | 是 | header和footer吸顶吸底样式。 |
