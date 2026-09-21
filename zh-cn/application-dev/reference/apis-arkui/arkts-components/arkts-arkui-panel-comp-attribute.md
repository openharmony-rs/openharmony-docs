# Panel属性/事件

```TypeScript
declare class PanelAttribute extends CommonMethod<PanelAttribute>
```

除支持[通用属性](arkts-arkui-common-comp.md#common)外，还支持以下属性：

除支持[通用事件](arkts-arkui-common-comp.md#common)外，还支持以下事件：

**继承/实现关系：** PanelAttribute extends CommonMethod<PanelAttribute>

**起始版本：** 7

**废弃版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundMask

```TypeScript
backgroundMask(color: ResourceColor)
```

指定Panel的背景蒙层。

> **说明：** 
> 
> 从API version 9开始支持，从API version 12开始废弃。建议使用

**起始版本：** 9

**废弃版本：** 12

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 指定Panel的背景蒙层。<br>默认值：'#08182431' |

## customHeight

```TypeScript
customHeight(value: Dimension | PanelHeight)
```

指定PanelType.CUSTOM状态下的高度。此属性仅在[type](#type)设置为PanelType.CUSTOM时生效，使用PanelHeight.WRAP_CONTENT时高度自适应内容，使用Dimension值时设置固定高度。

> **说明：** 
> 
> 从API version 10开始支持，从API version 12开始废弃。建议使用

**起始版本：** 10

**废弃版本：** 12

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; [PanelHeight](arkts-arkui-panel-comp-panelheight-e.md) | 是 | 指定PanelType.CUSTOM状态下的高度。<br>默认值：0 <br>**说明：** <br>不支持设置百分比，传入百分比时不生效。传入负数时不生效。 |

## dragBar

```TypeScript
dragBar(value: boolean)
```

设置是否存在控制条。

> **说明：** 
> 
> 从API version 7开始支持，从API version 12开始废弃。建议使用

**起始版本：** 7

**废弃版本：** 12

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置是否存在控制条，true表示存在，false表示不存在。<br>默认值：true |

## fullHeight

```TypeScript
fullHeight(value: number | string)
```

指定PanelMode.Full状态下的高度。

> **说明：** 
> 
> 从API version 7开始支持，从API version 12开始废弃。建议使用

**起始版本：** 7

**废弃版本：** 12

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number &#124; string | 是 | 指定PanelMode.Full状态下的高度。<br>默认值：当前组件主轴大小减去8vp空白区<br>单位：vp <br>**说明：** <br>不支持设置百分比。 |

## halfHeight

```TypeScript
halfHeight(value: number | string)
```

指定PanelMode.Half状态下的高度。

> **说明：** 
> 
> 此属性仅在type为Foldable或Temporary时生效。当type为Minibar时，Half模式不生效，halfHeight设置无效。
> 
> 从API version 7开始支持，从API version 12开始废弃。建议使用

**起始版本：** 7

**废弃版本：** 12

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number &#124; string | 是 | 指定PanelMode.Half状态下的高度。<br>默认值：当前组件主轴大小的一半。<br>单位：vp <br>**说明：** <br>不支持设置百分比。 |

## miniHeight

```TypeScript
miniHeight(value: number | string)
```

指定PanelMode.Mini状态下的高度。

> **说明：** 
> 
> 此属性仅在type为Minibar或Foldable时生效。当type为Temporary时，Mini模式不生效，miniHeight设置无效。
> 
> 从API version 7开始支持，从API version 12开始废弃。建议使用

**起始版本：** 7

**废弃版本：** 12

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number &#124; string | 是 | 指定PanelMode.Mini状态下的高度。<br>默认值：48 <br>单位：vp <br>**说明：** <br>不支持设置百分比。 |

## mode

```TypeScript
mode(value: PanelMode)
```

可滑动面板的初始状态。

> **说明：** 
> 
> 从API version 7开始支持，从API version 12开始废弃。建议使用

**起始版本：** 7

**废弃版本：** 12

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PanelMode](arkts-arkui-panel-comp-panelmode-e.md) | 是 | 设置可滑动面板的初始状态。<br>Minibar类型默认值：PanelMode.Mini；其余类型默认值：PanelMode.Half <br>从API version 10开始，该属性支持[$$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。 |

## onChange

```TypeScript
onChange(
    event: (
    /**
     * 内容区的宽度值，单位：vp。
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @FaAndStageModel
     * @atomicservice
     * @since 7 dynamiconly
     * @deprecated since 12
     */
      width: number,

    /**
     * 内容区的高度值，单位：vp。
     * 
     * 当dragBar属性为true时，Panel本身的高度值为dragBar高度加上内容区高度。
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @FaAndStageModel
     * @atomicservice
     * @since 7 dynamiconly
     * @deprecated since 12
     */
      height: number,

    /**
     * 面板的状态。
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @FaAndStageModel
     * @atomicservice
     * @since 7 dynamiconly
     * @deprecated since 12
     */
      mode: PanelMode,
    ) => void,
  )
```

当可滑动面板发生状态变化时触发。

**起始版本：** 7

**废弃版本：** 12

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (     /**      * 内容区的宽度值，单位：vp。      *      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @FaAndStageModel      * @atomicservice      * @since 7 dynamiconly      * @deprecated since 12      */       width: number,      /**      * 内容区的高度值，单位：vp。      *       * 当dragBar属性为true时，Panel本身的高度值为dragBar高度加上内容区高度。      *      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @FaAndStageModel      * @atomicservice      * @since 7 dynamiconly      * @deprecated since 12      */       height: number,      /**      * 面板的状态。      *      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @FaAndStageModel      * @atomicservice      * @since 7 dynamiconly      * @deprecated since 12      */       mode: PanelMode,     ) =&gt; void | 是 |  |

## onHeightChange

```TypeScript
onHeightChange(callback: (value: number) => void)
```

当可滑动面板发生高度变化时触发。

> **说明：** 
> 
> 从API version 9开始支持，从API version 12开始废弃。建议使用

**起始版本：** 9

**废弃版本：** 12

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: number) =&gt; void | 是 |  |

## show

```TypeScript
show(value: boolean)
```

当滑动面板弹出时调用。

> **说明：** 
> 
> 从API version 7开始支持，从API version 12开始废弃。建议使用

**起始版本：** 7

**废弃版本：** 12

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 当滑动面板弹出时调用，true显示面板，false不显示面板。<br>默认值：true <br>**说明：** <br>该属性的优先级高于参数show。 |

## showCloseIcon

```TypeScript
showCloseIcon(value: boolean)
```

设置是否显示关闭图标。

> **说明：** 
> 
> 从API version 10开始支持，从API version 12开始废弃。建议使用

**起始版本：** 10

**废弃版本：** 12

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置是否显示关闭图标，true表示显示，false表示不显示。<br>默认值：false |

## type

```TypeScript
type(value: PanelType)
```

可滑动面板的类型。type属性值制约其他属性的使用：当type为Minibar时，PanelMode.Half不生效；当type为Temporary时，PanelMode.Mini不生效；当type为CUSTOM时，不支持尺寸切换效果，需配合customHeight属性使用；当type为Foldable时，所有PanelMode值均可用，可配合fullHeight、halfHeight、miniHeight属性设置各状态高度。

> **说明：** 
> 
> 从API version 7开始支持，从API version 12开始废弃。建议使用

**起始版本：** 7

**废弃版本：** 12

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PanelType](arkts-arkui-panel-comp-paneltype-e.md) | 是 | 设置可滑动面板的类型。<br>默认值：PanelType.Foldable |
