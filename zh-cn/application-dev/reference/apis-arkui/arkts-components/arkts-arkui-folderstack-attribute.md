# FolderStack属性/事件

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** FolderStackAttribute extends [CommonMethod<FolderStackAttribute>](CommonMethod<FolderStackAttribute>)

**起始版本：** 11

<!--Device-unnamed-declare class FolderStackAttribute extends CommonMethod<FolderStackAttribute>--><!--Device-unnamed-declare class FolderStackAttribute extends CommonMethod<FolderStackAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignContent

```TypeScript
alignContent(value: Alignment)
```

设置子组件在容器内的对齐方式。该属性与[align](arkts-arkui-commonmethod-c.md#align)同时设置时，后设置的属性生效。
> **说明：**  
>  
> 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FolderStackAttribute-alignContent(value: Alignment): FolderStackAttribute--><!--Device-FolderStackAttribute-alignContent(value: Alignment): FolderStackAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Alignment](../arkts-apis/arkts-arkui-alignment-e.md) | 是 | 子组件在容器内的对齐方式。<br/>默认值：Alignment.Center <br />非法值：按默认值处理。 |

## autoHalfFold

```TypeScript
autoHalfFold(value: boolean)
```

设置是否开启自动旋转，仅在系统自动旋转关闭时该属性生效。
> **说明：**  
>  
> 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FolderStackAttribute-autoHalfFold(value: boolean): FolderStackAttribute--><!--Device-FolderStackAttribute-autoHalfFold(value: boolean): FolderStackAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否开启自动旋转。<br/>默认值：true，设置true表示FolderStack在半折叠状态（见[FoldStatus](../arkts-apis/arkts-arkui-foldstatus-e.md)）进行布局时开启自动旋转，设置false表示关闭自动旋转。该属性不区分设备类型。<br />非法值：按默认值处理。 |

## enableAnimation

```TypeScript
enableAnimation(value: boolean)
```

设置是否使用默认动效。
> **说明：**  
>  
> 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FolderStackAttribute-enableAnimation(value: boolean): FolderStackAttribute--><!--Device-FolderStackAttribute-enableAnimation(value: boolean): FolderStackAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否使用默认动效。<br/>默认值：true，设置true表示使用默认动效，设置false表示不使用默认动效。<br />非法值：按默认值处理。 |

## onFolderStateChange

```TypeScript
onFolderStateChange(callback: OnFoldStatusChangeCallback)
```

当前设备的折叠状态改变时触发回调，仅在横屏状态下生效。
> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FolderStackAttribute-onFolderStateChange(callback: OnFoldStatusChangeCallback): FolderStackAttribute--><!--Device-FolderStackAttribute-onFolderStateChange(callback: OnFoldStatusChangeCallback): FolderStackAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnFoldStatusChangeCallback](arkts-arkui-onfoldstatuschangecallback-t.md) | 是 | 当前设备的折叠状态改变时触发的回调。<br>**起始版本：** 18 |

## onHoverStatusChange

```TypeScript
onHoverStatusChange(handler: OnHoverStatusChangeCallback)
```

当前设备的悬停状态改变时触发回调。
> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FolderStackAttribute-onHoverStatusChange(handler: OnHoverStatusChangeCallback): FolderStackAttribute--><!--Device-FolderStackAttribute-onHoverStatusChange(handler: OnHoverStatusChangeCallback): FolderStackAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [OnHoverStatusChangeCallback](arkts-arkui-onhoverstatuschangecallback-t.md) | 是 | 当前设备的悬停状态改变时触发的回调。<br>**起始版本：** 18 |

