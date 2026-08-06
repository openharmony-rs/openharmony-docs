# DepthComponentAttribute（系统接口）

除支持[通用属性]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_外，还支持以下属性：

**继承/实现关系：** DepthComponentAttribute extends [CommonMethod](common-commonmethod-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface DepthComponentAttribute extends CommonMethod--><!--Device-unnamed-export declare interface DepthComponentAttribute extends CommonMethod-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## camera

```TypeScript
default camera(camera: DepthCameraParams): this
```

设置景深渲染使用的相机参数。 > **说明：** > > 以图片作为背景时，相机参数更新不会引起背景的变化。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DepthComponentAttribute-default camera(camera: DepthCameraParams): this--><!--Device-DepthComponentAttribute-default camera(camera: DepthCameraParams): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| camera | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 相机参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## depthMap

```TypeScript
default depthMap(depthMap: ResourceStr | PixelMap, callback?: DepthMapCallback): this
```

设置用于景深计算和渲染的深度图。使用callback异步回调。 > **说明：** > > - 深度图是用于描述在3D空间中，背景中每个像素点与相机距离的二维矩阵图像。 > > - 其数据格式为灰阶图，灰度值越大（颜色越白）的像素点距离相机越近。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DepthComponentAttribute-default depthMap(depthMap: ResourceStr | PixelMap, callback?: DepthMapCallback): this--><!--Device-DepthComponentAttribute-default depthMap(depthMap: ResourceStr | PixelMap, callback?: DepthMapCallback): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| depthMap | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| PixelMap | 是 | 深度图资源或PixelMap对象，引用方式与静态背景图一致。仅背景为静态图时需要设置深度图。深度图需要与背景图的分辨率保持一致。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 深度图加载完成时的回调函数。加载成功时error.code为0，加载失败时error中包含错误码和错误信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## light

```TypeScript
default light(light: DepthLightParams): this
```

设置景深渲染使用的光照参数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DepthComponentAttribute-default light(light: DepthLightParams): this--><!--Device-DepthComponentAttribute-default light(light: DepthLightParams): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| light | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 光照参数，包含方向、颜色和强度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onComplete

```TypeScript
default onComplete(callback: DepthComponentCompleteCallback): this
```

背景资源加载成功时触发该回调。使用callback异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DepthComponentAttribute-default onComplete(callback: DepthComponentCompleteCallback): this--><!--Device-DepthComponentAttribute-default onComplete(callback: DepthComponentCompleteCallback): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 背景资源加载成功的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onError

```TypeScript
default onError(callback: DepthComponentErrorCallback): this
```

背景资源加载出现错误时触发该回调。使用callback异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DepthComponentAttribute-default onError(callback: DepthComponentErrorCallback): this--><!--Device-DepthComponentAttribute-default onError(callback: DepthComponentErrorCallback): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 背景资源加载失败的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setDepthComponentOptions

```TypeScript
default setDepthComponentOptions(background: ResourceStr | PixelMap, options?: DepthComponentOptions): this
```

Set DepthComponent options.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DepthComponentAttribute-default setDepthComponentOptions(background: ResourceStr | PixelMap, options?: DepthComponentOptions): this--><!--Device-DepthComponentAttribute-default setDepthComponentOptions(background: ResourceStr | PixelMap, options?: DepthComponentOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| background | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| PixelMap | 是 | Background resource (required). |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | DepthComponent options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | Returns instance of DepthComponentAttribute. |

