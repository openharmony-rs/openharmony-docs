# Panel属性/事件

窗格属性。@extends CommonMethod&lt;PanelAttribute&gt;

**继承/实现关系：** PanelAttribute extends CommonMethod<PanelAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## backgroundMask

```TypeScript
backgroundMask(color: ResourceColor)
```

指定Panel的背景蒙层。

**起始版本：** 9

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 指定Panel的背景蒙层。 |

## customHeight

```TypeScript
customHeight(value: Dimension | PanelHeight)
```

指定PanelType.CUSTOM状态下的高度。

**起始版本：** 10

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) \| [PanelHeight](arkts-arkui-panelheight-e.md) | 是 | 指定PanelType.CUSTOM状态下的高度。 |

## dragBar

```TypeScript
dragBar(value: boolean)
```

设置是否存在控制条。

**起始版本：** 7

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置是否存在控制条，true表示存在，false表示不存在。 |

## fullHeight

```TypeScript
fullHeight(value: number | string)
```

指定PanelType.Full状态下的高度。

**起始版本：** 7

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 指定PanelMode.Full状态下的高度。 |

## halfHeight

```TypeScript
halfHeight(value: number | string)
```

指定PanelMode.Half状态下的高度。

**起始版本：** 7

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 指定PanelMode.Half状态下的高度。 |

## miniHeight

```TypeScript
miniHeight(value: number | string)
```

指定PanelMode.Mini状态下的高度。

**起始版本：** 7

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 指定PanelMode.Mini状态下的高度。 |

## mode

```TypeScript
mode(value: PanelMode)
```

可滑动面板的初始状态。

**起始版本：** 7

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PanelMode](arkts-arkui-panelmode-e.md) | 是 | 设置可滑动面板的初始状态。 |

## onChange

```TypeScript
onChange(
    event: (
    /**
     * Width of content area.
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @since 7
     */
    /**
     * Width of content area.
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @FaAndStageModel
     * @atomicservice
     * @since 11 dynamiconly
     * @deprecated since 12
     */
      width: number,

    /**
     * Height of content area.
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @since 7
     */
    /**
     * Height of content area.
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @FaAndStageModel
     * @atomicservice
     * @since 11 dynamiconly
     * @deprecated since 12
     */
      height: number,

    /**
     * Initial state.
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @since 7
     */
    /**
     * Initial state.
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @FaAndStageModel
     * @atomicservice
     * @since 11 dynamiconly
     * @deprecated since 12
     */
      mode: PanelMode,
    ) => void,
  )
```

当可滑动面板发生状态变化时触发。

**起始版本：** 7

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (     /**      * Width of content area.      *      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @since 7      */     /**      * Width of content area.      *      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @FaAndStageModel      * @atomicservice      * @since 11 dynamiconly      * @deprecated since 12      */       width: number,      /**      * Height of content area.      *      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @since 7      */     /**      * Height of content area.      *      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @FaAndStageModel      * @atomicservice      * @since 11 dynamiconly      * @deprecated since 12      */       height: number,      /**      * Initial state.      *      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @since 7      */     /**      * Initial state.      *      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @FaAndStageModel      * @atomicservice      * @since 11 dynamiconly      * @deprecated since 12      */       mode: PanelMode,     ) = & gt; void | 是 |  |

## onHeightChange

```TypeScript
onHeightChange(callback: (value: number) => void)
```

当可滑动面板发生高度变化时触发。

**起始版本：** 9

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: number) = & gt; void | 是 |  |

## show

```TypeScript
show(value: boolean)
```

当滑动面板弹出时调用。

**起始版本：** 7

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 当滑动面板弹出时调用，true显示面板，false不显示面板。 |

## showCloseIcon

```TypeScript
showCloseIcon(value: boolean)
```

设置是否显示关闭图标。

**起始版本：** 10

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置是否显示关闭图标，true表示显示，false表示不显示。 |

## type

```TypeScript
type(value: PanelType)
```

可滑动面板的类型。

**起始版本：** 7

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PanelType](arkts-arkui-paneltype-e.md) | 是 | 设置可滑动面板的类型。 |
