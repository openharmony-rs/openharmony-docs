# FolderStack属性/事件

In addition to the [universal events](arkts-arkui-commonmethod-c.md), the following events are supported.

**继承/实现关系：** FolderStackAttribute extends CommonMethod<FolderStackAttribute>

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## alignContent

```TypeScript
alignContent(value: Alignment)
```

设置子组件在容器内的对齐方式，调用后子组件按照指定的对齐方式在容器内排列。该属性与align同时设置时，后设置的属性生效。

> **说明：**
> 
> 从API version 12开始，该接口支持在attributeModifier中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Alignment](../arkts-apis/arkts-arkui-alignment-e.md) | 是 | 子组件在容器内的对齐方式，取值包括TopStart、Top、TopEnd、Start、Center、End、BottomStart、Bottom、BottomEnd。 默认值：Alignment.Center 非法值：按默认值处理。 |

## autoHalfFold

```TypeScript
autoHalfFold(value: boolean)
```

设置在半折叠状态下是否开启FolderStack组件的自动旋转。当系统自动旋转开关关闭时，可通过该属性控制FolderStack在半折叠状态下是否进行自动旋转。典型使用场景：当用户在系统设置中关闭自动旋转功能后，希望在折叠屏设备半折叠状态下仍然能够根据折叠状态自动调整应用布局方向。

> **说明：**
> 
> 从API version 12开始，该接口支持在attributeModifier中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否开启自动旋转。 默认值：true。设置为true时，FolderStack在半折叠状态（见FoldStatus）进行布局时自动旋转；设置为false时，FolderStack在半折叠状态下不 会自动旋转。仅在系统自动旋转关闭时生效；系统自动旋转开启时，此属性不生效，FolderStack遵循系统旋转行为。该参数仅在双折叠设备上生效，当FolderStack的父组件为if/else条件渲染节点时，该参数将失效。 非法值：按默认值处理。 |

## enableAnimation

```TypeScript
enableAnimation(value: boolean)
```

设置是否使用默认动效，调用后启用或禁用FolderStack的默认悬停动画效果。

> **说明：**
> 
> 从API version 12开始，该接口支持在attributeModifier中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否使用默认动效。 默认值：true，设置true表示使用默认动效，设置false表示不使用默认动效。 非法值：按默认值处理。 |

## onFolderStateChange

```TypeScript
onFolderStateChange(callback: OnFoldStatusChangeCallback)
```

当前设备的折叠状态改变时触发回调<!--RP3-->（该回调仅在横屏状态下生效）<!--RP3End-->。典型使用场景：根据折叠状态调整应用布局，例如在展开状态下显示双栏布局，在半折叠状态下调整上半屏和下半屏的内容分布。

> **说明：**
> 
> 从API version 20开始，该接口支持在attributeModifier中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnFoldStatusChangeCallback](arkts-arkui-onfoldstatuschangecallback-t.md) | 是 | 当前设备的折叠状态改变时触发的回调。<br>**起始版本：** 18 |

## onHoverStatusChange

```TypeScript
onHoverStatusChange(handler: OnHoverStatusChangeCallback)
```

当前设备的悬停状态改变时触发回调。典型使用场景：根据悬停状态调整应用布局和交互逻辑，例如在悬停模式下优化上半屏和下半屏的内容展示。

> **说明：**
> 
> 从API version 20开始，该接口支持在attributeModifier中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [OnHoverStatusChangeCallback](arkts-arkui-onhoverstatuschangecallback-t.md) | 是 | 当前设备的悬停状态改变时触发的回调。<br>**起始版本：** 18 |
