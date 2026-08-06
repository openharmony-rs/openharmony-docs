# DrawableDescriptor

父类对象提供可重写的方法，包含：获取[PixelMap]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_实例，图片资源加载能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class DrawableDescriptor--><!--Device-unnamed-export declare class DrawableDescriptor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getPixelMap

```TypeScript
getPixelMap(): image.PixelMap | undefined
```

获取PixelMap实例。 > **说明：** > > DrawableDescriptor对象通过[release]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_释放后，本接口返回undefined。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DrawableDescriptor-getPixelMap(): image.PixelMap | undefined--><!--Device-DrawableDescriptor-getPixelMap(): image.PixelMap | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| image.PixelMap | - Return the PixelMap of the calling DrawableDescriptor object. |

## invalidate

```TypeScript
invalidate(): void
```

重新绘制DrawableDescriptor。当前仅支持 [PictureDrawableDescriptor]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类型，其他DrawableDescriptor子类型触发后无效果。 若DrawableDescriptor未绑定任何组件，则不会执行任何操作。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DrawableDescriptor-invalidate(): void--><!--Device-DrawableDescriptor-invalidate(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isReleased

```TypeScript
isReleased(): boolean
```

查询DrawableDescriptor是否已被释放。返回true表示已释放，此时调用 [getPixelMap]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_、 [getForeground]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、 [getBackground]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_、 [getMask]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_、 [loadSync]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_、 [load]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_等接口，返回undefined或默认异常值；返回false表示未释放，对象可正常使用。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DrawableDescriptor-isReleased(): boolean--><!--Device-DrawableDescriptor-isReleased(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | DrawableDescriptor是否已被释放。true表示已释放，false表示未释放。 |

## load

```TypeScript
load(): Promise<DrawableDescriptorLoadedResult>
```

发起图片资源的异步加载，并返回加载结果。使用Promise异步回调。 > **说明：** > > DrawableDescriptor对象通过[release]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_释放后，本接口返回imageWidth和imageHeight均为 > -1的Promise结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DrawableDescriptor-load(): Promise<DrawableDescriptorLoadedResult>--><!--Device-DrawableDescriptor-load(): Promise<DrawableDescriptorLoadedResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DrawableDescriptorLoadedResult&gt; | - 图片资源的加载结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [111001](../errorcode-drawable-descriptor.md#111001-资源加载失败) | resource loading failed. |

## loadSync

```TypeScript
loadSync(): DrawableDescriptorLoadedResult
```

发起图片资源的同步加载，并返回加载结果。 > **说明：** > > DrawableDescriptor对象通过[release]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_释放后，本接口返回imageWidth和imageHeight均为 > -1的结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DrawableDescriptor-loadSync(): DrawableDescriptorLoadedResult--><!--Device-DrawableDescriptor-loadSync(): DrawableDescriptorLoadedResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | - 图片资源的加载结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [111001](../errorcode-drawable-descriptor.md#111001-资源加载失败) | resource loading failed. |

## release

```TypeScript
release(): void
```

释放DrawableDescriptor持有的资源。调用release后，该对象将不可用，再调用 [getPixelMap]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_、 [getForeground]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、 [getBackground]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_、 [getMask]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_、 [loadSync]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_、 [load]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_等接口，返回undefined或默认异常值。重复调用release不会崩溃。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DrawableDescriptor-release(): void--><!--Device-DrawableDescriptor-release(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

