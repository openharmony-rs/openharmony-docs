# XComponent属性/事件

定义XComponentAttribute。 除通用属性外，还支持以下属性。 从API版本12开始，当type设置为**SURFACE**或**TEXTURE**时，支持通用事件。

**继承/实现关系：** XComponentAttribute extends CommonMethod<XComponentAttribute>

**起始版本：** 8

<!--Device-unnamed-declare class XComponentAttribute--><!--Device-unnamed-declare class XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## enableAnalyzer

```TypeScript
enableAnalyzer(enable: boolean)
```

设置是否启用AI图像分析器，支持主体识别、文字识别和查找对象。 要使设置生效，此属性必须与XComponentController的[StartImageAnalyzer](arkts-arkui-xcomponentcontroller-c.md#startimageanalyzer)和[StopImageAnalyzer](arkts-arkui-xcomponentcontroller-c.md#stopimageanalyzer)一起使用。 此特性不能与[overlay](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-overlay.md#overlay)属性同时使用。 如果两者都设置，overlay中的CustomBuilder属性将不生效。此特性还依赖于设备能力。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentAttribute-enableAnalyzer(enable: boolean): XComponentAttribute--><!--Device-XComponentAttribute-enableAnalyzer(enable: boolean): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用AI图像分析器。<br>**true**：启用；**false**：禁用。<br> 默认值：**false**。 |

## enableSecure

```TypeScript
enableSecure(isSecure: boolean)
```

设置是否启用安全surface，以保护组件内渲染的内容不被截屏或录屏。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentAttribute-enableSecure(isSecure: boolean): XComponentAttribute--><!--Device-XComponentAttribute-enableSecure(isSecure: boolean): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isSecure | boolean | 是 | 是否启用安全surface。<br>值**true**表示启用安全surface，**false**表示相反的情况。<br> 默认值：**false**。 |

## hdrBrightness

```TypeScript
hdrBrightness(brightness: number, type?: HdrType)
```

用于调整组件显示HDR内容时的亮度。<br/>当参数type设置为非**HdrType**.DEFAULT时，调用该接口前需先检查Display的hdrFormats属性是否包含对应的HDRFormat。 仅当hdrFormats包含对应的HDRFormat时，当前设备才支持对应的HDR类型，参数设置才会生效；否则将使用默认值**HdrType**.DEFAULT。 其映射关系如下：<br/>| type取值 | hdrFormats需包含的HDRFormat | <br/>| -------- | -------- | <br/>| **HdrType**.AIHDR | HDRFormat.VIDEO_AIHDR | **说明：** 仅XComponent构造参数中的type为**XComponentType**.SURFACE时该接口生效，否则该接口不生效。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentAttribute-hdrBrightness(brightness: number, type?: HdrType): XComponentAttribute--><!--Device-XComponentAttribute-hdrBrightness(brightness: number, type?: HdrType): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brightness | number | 是 | HDR内容的亮度。<br/>取值范围：[0.0, 1.0]。小于0.0的值按0.0处理，大于1.0的值按1.0处理，其他异常值按1.0处理。 <br/>**0.0**表示内容按照SDR亮度显示，**1.0**表示内容按照当前允许的最高HDR亮度显示。<br/>默认值：**1.0**。 |
| type | [HdrType](arkts-arkui-hdrtype-e.md) | 否 | 显示HDR内容时的HDR类型。<br/>默认值：**HdrType.DEFAULT |

## onDestroy

```TypeScript
onDestroy(event: VoidCallback)
```

当插件销毁时触发。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentAttribute-onDestroy(event: VoidCallback): XComponentAttribute--><!--Device-XComponentAttribute-onDestroy(event: VoidCallback): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | XComponent销毁后的回调。<br>**起始版本：** 18 |

## onLoad

```TypeScript
onLoad(callback: OnNativeLoadCallback)
```

插件加载完成时回调事件。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentAttribute-onLoad(callback: OnNativeLoadCallback): XComponentAttribute--><!--Device-XComponentAttribute-onLoad(callback: OnNativeLoadCallback): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnNativeLoadCallback](arkts-arkui-onnativeloadcallback-t.md) | 是 | 插件加载完成时回调事件，用于获取XComponent实例对象的context。<br>**起始版本：** 18 |

