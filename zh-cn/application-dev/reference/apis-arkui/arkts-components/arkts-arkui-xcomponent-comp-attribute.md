# XComponent属性/事件

```TypeScript
declare class XComponentAttribute extends CommonMethod<XComponentAttribute>
```

定义XComponentAttribute。

除通用属性外，还支持以下属性。

从API版本12开始，当type设置为**SURFACE**或**TEXTURE**时，支持[通用事件](arkts-arkui-common-comp.md#common)。

**继承/实现关系：** XComponentAttribute extends CommonMethod<XComponentAttribute>

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableAnalyzer

```TypeScript
enableAnalyzer(enable: boolean)
```

设置组件支持AI分析，当前支持主体识别、文字识别和对象查找等功能。本功能需要搭配XComponentController的startImageAnalyzer和stopImageAnalyzer一起使用。不能和overlay属性同时使用，两者同时设置时overlay中CustomBuilder属性将失效。AI分析功能依赖设备能力。  
> **说明：** 
> 
> 仅type为SURFACE或TEXTURE时该功能有效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用AI分析功能。<br>true：开启AI分析；false：关闭AI分析。<br>默认值：false |

## enableSecure

```TypeScript
enableSecure(isSecure: boolean)
```

防止组件内自绘制内容被截屏、录屏。  
> **说明：** 
> 
> 仅type为SURFACE时有效。
> 
> 不支持ArkUI NDK接口创建的XComponent组件。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isSecure | boolean | 是 | 是否开启隐私图层模式。<br>true：开启隐私图层模式；false：关闭隐私图层模式。<br>默认值：false |

## hdrBrightness

```TypeScript
hdrBrightness(brightness: number)
```

用于调整组件播放HDR视频的亮度。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brightness | number | 是 | HDR视频的亮度。<br>默认值：1.0<br>取值范围：[0.0, 1.0]。小于0.0的值按0.0处理，大于1.0的值按1.0处理，其他异常值按1.0处理。<br>0.0表示视频按照SDR亮度显示，1.0表示视频按照当前允许的最高HDR亮度显示。 |

<a id="hdrbrightness-1"></a>

## hdrBrightness

```TypeScript
hdrBrightness(brightness: number, type?: HdrType)
```

用于调整组件播放HDR视频的亮度。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brightness | number | 是 | HDR视频的亮度。<br>默认值：1.0<br>取值范围：[0.0, 1.0]。小于0.0的值按0.0处理，大于1.0的值按1.0处理，其他异常值按1.0处理。<br>0.0表示视频按照SDR亮度显示，1.0表示视频按照当前允许的最高HDR亮度显示。 |
| type | [HdrType](arkts-arkui-xcomponent-comp-hdrtype-e.md) | 否 | 显示HDR内容时的HDR类型。<br>默认值：**HdrType.DEFAULT** |

## onDestroy

```TypeScript
onDestroy(event: VoidCallback)
```

Native卸载完成时回调事件。与onSurfaceDestroyed的区别：onDestroy适用于设置libraryname参数的场景，回调无参数；onSurfaceDestroyed适用于未设置libraryname参数的场景，回调参数为surfaceId。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | Native卸载完成时回调事件。<br>**适用版本：** 18 |

## onLoad

```TypeScript
onLoad(callback: OnNativeLoadCallback)
```

Native加载完成时回调事件。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnNativeLoadCallback](arkts-arkui-xcomponent-comp-onnativeloadcallback-t.md) | 是 | Native加载完成时回调事件，用于获取XComponent实例对象的context。<br>**适用版本：** 18 |
