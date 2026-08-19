# DepthComponentAttribute（系统接口）

除支持通用属性外，还支持以下属性：

**继承/实现关系：** DepthComponentAttribute extends CommonMethod

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface DepthComponentAttribute--><!--Device-unnamed-export declare interface DepthComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## camera

```TypeScript
camera(camera: DepthCameraParams): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-DepthComponentAttribute-camera(camera: DepthCameraParams): this--><!--Device-DepthComponentAttribute-camera(camera: DepthCameraParams): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| camera | [DepthCameraParams](arkts-na-depthcomponent-depthcameraparams-i-sys.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## depthMap

```TypeScript
depthMap(depthMap: ResourceStr | PixelMap, callback?: DepthMapCallback): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-DepthComponentAttribute-depthMap(depthMap: ResourceStr | PixelMap, callback?: DepthMapCallback): this--><!--Device-DepthComponentAttribute-depthMap(depthMap: ResourceStr | PixelMap, callback?: DepthMapCallback): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| depthMap | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) | 是 |  |
| callback | [DepthMapCallback](arkts-na-depthmapcallback-t-sys.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## light

```TypeScript
light(light: DepthLightParams): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-DepthComponentAttribute-light(light: DepthLightParams): this--><!--Device-DepthComponentAttribute-light(light: DepthLightParams): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| light | [DepthLightParams](arkts-na-depthcomponent-depthlightparams-i-sys.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onComplete

```TypeScript
onComplete(callback: DepthComponentCompleteCallback): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-DepthComponentAttribute-onComplete(callback: DepthComponentCompleteCallback): this--><!--Device-DepthComponentAttribute-onComplete(callback: DepthComponentCompleteCallback): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [DepthComponentCompleteCallback](arkts-na-depthcomponentcompletecallback-t-sys.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onError

```TypeScript
onError(callback: DepthComponentErrorCallback): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-DepthComponentAttribute-onError(callback: DepthComponentErrorCallback): this--><!--Device-DepthComponentAttribute-onError(callback: DepthComponentErrorCallback): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [DepthComponentErrorCallback](arkts-na-depthcomponenterrorcallback-t-sys.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setDepthComponentOptions

```TypeScript
setDepthComponentOptions(background: ResourceStr | PixelMap, options?: DepthComponentOptions): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-DepthComponentAttribute-setDepthComponentOptions(background: ResourceStr | PixelMap, options?: DepthComponentOptions): this--><!--Device-DepthComponentAttribute-setDepthComponentOptions(background: ResourceStr | PixelMap, options?: DepthComponentOptions): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| background | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) | 是 |  |
| options | [DepthComponentOptions](arkts-na-depthcomponent-depthcomponentoptions-i-sys.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

