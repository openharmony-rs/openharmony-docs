# ImageAnalyzerController

图像AI分析控制器。可以将此对象绑定至支持的组件，并通过该控制器调用其提供的方法。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare class ImageAnalyzerController--><!--Device-unnamed-declare class ImageAnalyzerController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

构造函数。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAnalyzerController-constructor()--><!--Device-ImageAnalyzerController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getImageAnalyzerSupportTypes

```TypeScript
getImageAnalyzerSupportTypes(): ImageAnalyzerType[]
```

获取此控制器已绑定组件所支持的AI分析类型。调用前需先通过 Image/ImageAnimator 等组件的 aiController 属性将本控制器绑定到组件，否则返回空数组。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAnalyzerController-getImageAnalyzerSupportTypes(): ImageAnalyzerType[]--><!--Device-ImageAnalyzerController-getImageAnalyzerSupportTypes(): ImageAnalyzerType[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_[] | 对应组件支持的AI分析类型。 |

